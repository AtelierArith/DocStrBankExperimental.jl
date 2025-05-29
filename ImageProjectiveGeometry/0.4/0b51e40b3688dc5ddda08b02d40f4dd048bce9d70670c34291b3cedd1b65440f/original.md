Camera - Structure defining parameters of a camera following the Brown          distortion model

```
      fx::Float64      # Focal length.
      fy::Float64
     ppx::Float64      # Principal point.
     ppy::Float64
      k1::Float64      # Radial lens distortion parameters.
      k2::Float64
      k3::Float64
      p1::Float64      # Tangential lens distortion parameters.
      p2::Float64
    skew::Float64
    rows::Integer   # Optional, providing rows and columns allows detection
    cols::Integer   # of points being projected out of image bounds.
       P::Array     # Camera position in world coordinates.
    Rc_w::Array     # Rotation matrix defining world orientation with
                    # respect to the camera frame.
```

Note the ordering of the tangential distortion parameters p1 and p2 is not always consistent in the literature.  Within cameraproject() they are used in the following order, where x and y refer to column and row coordinates repectively.

```
   dx = 2*p1*x*y          +  p2*(r^2 + 2*x^2)
   dy = p1*(r^2 + 2*y^2)  +  2*p2*x*y

```

Constructors:

```
      Camera(keyword = value, ....)

      Camera(P)     # Where P is a 3x4 projection matrix.
                    # In this case only fx, fy, skew, P and Rc_w can be defined,
                    # all other (distortion) parameters are set to 0.
```
