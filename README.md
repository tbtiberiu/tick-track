# TickTrack

## Overview

TickTrack is a Python project designed to detect and interpret the time displayed on an analog clock from an image. The project leverages computer vision techniques to process the input image, identify clock components, and calculate the time. This tool is ideal for automating time-reading tasks or serving as a foundation for advanced computer vision projects involving analog clock recognition.

---

## Algorithm Steps to Get the Time

1. **Image Preprocessing:**

   - Resize the input image to ensure it fits the processing requirements.
   - Convert the image to grayscale if it is in color.
   - Apply a bilateral filter to reduce noise while preserving edges.

2. **Clock Detection:**

   - Detect the circular contour of the clock using the Hough Circle Transform.
   - Extract the center coordinates and radius of the detected circle.

3. **Line Detection:**

   - Apply a binary threshold to the grayscale image to enhance line detection.
   - Use the Hough Line Transform to identify straight lines in the thresholded image.

4. **Line Filtering:**

   - Remove lines that extend outside the clock's boundary.
   - Ensure all retained lines are fully within the detected circular contour.

5. **Line Merging:**

   - Normalize line coordinates for consistency.
   - Merge parallel or overlapping lines based on distance and angle thresholds.

6. **Clock Hands Identification:**

   - Identify the hour and minute hands based on their lengths (shorter for the hour hand, longer for the minute hand).
   - Normalize line orientation relative to the clock center for accurate angle calculation.

7. **Time Calculation:**

   - Calculate the angles of the clock hands relative to the vertical.
   - Convert these angles into time values:
     - Minute: Each minute corresponds to 6 degrees.
     - Hour: Each hour corresponds to 30 degrees, adjusted for the minute hand's position.

8. **Result Visualization:**
   - Overlay detected clock components (circle, hour hand, minute hand) on the original image.
   - Display the calculated time.

---

## Testing and Limitations

TickTrack has been tested on a variety of images, including:

- Simple clocks with clear, distinguishable hands.
- Clocks with different background colors and textures.

**Limitations:**

- May struggle with highly complex backgrounds or clocks with unconventional designs.
- Performance may vary based on image quality and resolution.
- Clocks must have a circular frame.
