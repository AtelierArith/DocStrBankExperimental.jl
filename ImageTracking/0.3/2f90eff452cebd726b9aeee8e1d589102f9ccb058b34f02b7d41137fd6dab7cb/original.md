```
coordinates = haar_coordinates(height, width, feat)
```

Returns an array containing the coordinates of the Haar-like features of the specified type.

The caller of the haar_coordinates function specifies a rectangular region in the image by its height and width and a particular feature type, e.g. two rectangles side by side (:x2). This function then computes the coordinates for the particular rectangle configuration for all possible locations, and all possible rectangle widths & heights.

Parameters:

  * height        = Height of the neighbourhood/window where the coordinates are computed
  * width         = Width of the neighbourhood/window where the coordinates are computed
  * feat          = A symbol specifying the type of the Haar-like feature to be found

```
    Currently, feat can take 5 values:

    :x2 = Two rectangles along horizontal axis
        +---------------------------------------+
        |                                       |
        | +-----+-----+                         |
        | |     |     |                         |
        | | -1  | +1  |  +---------->           |
        | |     |     |                         |
        | +-----+-----+                         |
        |                                       |
        |       +                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       v                               |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        +---------------------------------------+

    :y2 = Two rectangles along vertical axis
        +---------------------------------------+
        |                                       |
        | +------------+                        |
        | |     -1     |                        |
        | +------------+  +---------->          |
        | |     +1     |                        |
        | +------------+                        |
        |                                       |
        |       +                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       v                               |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        +---------------------------------------+

    :x3 = Three rectangles along horizontal axis
        +---------------------------------------+
        |                                       |
        | +-----+-----+-----+                   |
        | |     |     |     |                   |
        | | -1  | +1  | -1  |  +---------->     |
        | |     |     |     |                   |
        | +-----+-----+-----+                   |
        |                                       |
        |       +                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       v                               |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        +---------------------------------------+

    :y3 = Three rectangles along vertical axis
        +---------------------------------------+
        |                                       |
        | +------------+                        |
        | |     -1     |                        |
        | +------------+                        |
        | |     +1     |  +---------->          |
        | +------------+                        |
        | |     -1     |                        |
        | +------------+                        |
        |                                       |
        |       +                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       v                               |
        |                                       |
        |                                       |
        |                                       |
        |                                       |
        +---------------------------------------+

    :xy4 = Four rectangles along horizontal and vertical axes
        +---------------------------------------+
        |                                       |
        | +-----+-----+                         |
        | |     |     |                         |
        | | -1  | +1  |                         |
        | |     |     |                         |
        | +-----+-----+  +---------->           |
        | |     |     |                         |
        | | +1  | -1  |                         |
        | |     |     |                         |
        | +-----+-----+                         |
        |                                       |
        |       +                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       |                               |
        |       v                               |
        |                                       |
        |                                       |
        +---------------------------------------+

    The +1 and -1 signs show which rectangles are subtracted and which are added to evaluate the final haar feature.

```
