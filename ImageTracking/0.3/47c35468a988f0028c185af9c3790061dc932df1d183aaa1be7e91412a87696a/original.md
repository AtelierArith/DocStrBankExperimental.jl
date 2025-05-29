```
features = haar_features(img, top_left, bottom_right, feat)
features = haar_features(img, top_left, bottom_right, feat, coordinates)
```

Returns an array containing the Haar-like features for the given Integral Image in the region specified by the points top*left and bottom*right.

The caller of the haar*features function specifies a rectangular region in the image by its top*left and bottom_right points and a particular feature type, e.g. two rectangles side by side (:x2). This function then computes the values of all haar rectangular features for the particular rectangle configuration for all possible locations, and all possible rectangle widths & heights if coordinates of certain specific features are not provided. If they are provided then it only computes the values of those features whose coordinates are given. Calculating value of haar rectangular feature corresponds to finding the difference of sums of all points in the different rectangles comprising the feature.

Parameters:

  * img               = The Integral Image for which the Haar-like features are to be found
  * top_left          = The top and left most point of the region where the features are to be found
  * bottom_right      = The bottom and right most point of the region where the features are to be found
  * feat              = A symbol specifying the type of the Haar-like feature to be found

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

  * coordinates       = The user can provide the coordinates of the rectangles if only certain Haar-like features are to found in the given region. The required format is a 3 Dimensional array as (f,r,4) where f = number*of*features, r = number*of*rectangles and 4 is for the coordinates of the top*left and bottom*right point of the rectangle (top*left*y, top*left*x, bottom*right*y, bottom*right*x). The default value is nothing, where all the features are found

## References

M. Oren, C. Papageorgiou, P. Sinha, E. Osuna and T. Poggio, "Pedestrian detection using wavelet templates," Proceedings of IEEE Computer Society Conference on Computer Vision and Pattern Recognition, San Juan, 1997, pp. 193-199.

P. Viola and M. Jones, "Rapid object detection using a boosted cascade of simple features," Proceedings of the 2001 IEEE Computer Society Conference on Computer Vision and Pattern Recognition. CVPR 2001, 2001, pp. I-511-I-518 vol.1.
