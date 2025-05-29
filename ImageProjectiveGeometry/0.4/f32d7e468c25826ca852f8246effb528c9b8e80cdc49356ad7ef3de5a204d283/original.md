decomposecamera -  Decomposition of a camera projection matrix

```
Usage:  K, Rc_w, Pc, pp, pv = decomposecamera(P)

   P is decomposed into the form P = K*(R -R*Pc)

Argument:  P - 3 x 4 camera projection matrix
Returns:
           K - Calibration matrix of the form
                 |  ax   s   ppx |
                 |   0   ay  ppy |
                 |   0   0    1  |

               Where:
               ax = f/pixel_width and ay = f/pixel_height,
               ppx and ppy define the principal point in pixels,
               s is the camera skew.
        Rc_w - 3 x 3 rotation matrix defining the world coordinate frame
               in terms of the camera frame. Columns of R transposed define
               the directions of the camera X, Y and Z axes in world
               coordinates.
          Pc - Camera centre position in world coordinates.
          pp - Image principal point.
          pv - Principal vector  from the camera centre C through pp
               pointing out from the camera.  This may not be the same as
               R'(:,3) if the principal point is not at the centre of the
               image, but it should be similar.
```

See also: rq3()
