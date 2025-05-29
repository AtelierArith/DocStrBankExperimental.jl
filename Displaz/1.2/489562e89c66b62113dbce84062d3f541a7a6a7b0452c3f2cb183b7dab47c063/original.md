```
viewplot([plotobj::DisplazWindow=current()];
         center=point_or_label, radius=dist_from_center, rotation=rot_matrix)
```

Set the point of view of the 3D camera.  The camera model is designed to view an object at a given `center` of rotation, with rotations pivoting around that position.

If not specified, `plotobj` is the current plot window.  Keyword arguments define the camera view as follows:

  * The `center` argument may be a 3D point or the label of a data set. If a label is supplied the centroid of the associated dataset will be used.
  * The `radius` argument should be a number giving the distance that the camera will be away from the center of rotation.
  * The `rotation` argument specifies the angles at which the camera will view the scene. This can be a matrix transforming points into the standard OpenGL camera coordinates (+x right, +y up, -z into the scene). Alternatively you may supply a tuple `(yaw, pitch, roll)` in degrees which is equivalent to using the rotation matrix `RotZXZ(deg2rad(roll), deg2rad(pitch-90), deg2rad(yaw))` from Rotations.jl.
