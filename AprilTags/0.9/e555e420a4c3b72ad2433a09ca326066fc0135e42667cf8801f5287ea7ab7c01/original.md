```
homography_to_pose(H, f_width, f_height, c_width, c_height, [taglength = 2.0])
```

Given a 3x3 homography matrix and the camera model (focal length and centre), compute the pose of the tag.

Notes

  * Images.jl uses `::Array` in Julia as column-major (i.e. vertical major) convention, that is `size(img) == (480, 640)`

      * Axes start top left-corner of the image plane (i.e. the image-frame):
      * `width` is from left to right,
      * `height` is from top downward.
  * The low-level `ccall` wrapped C-library underneath uses the convention (i.e. the camera-frame): 

      * `fx == f_width`,
      * `cy == c_height`, and
      * C-library camara coordinate system: camera looking along positive Z axis with `x` to the right and `y` down.

          * C-library internally follows: https://docs.opencv.org/3.4/d9/d0c/group__calib3d.html
  * The focal lengths should be given in pixels.
  * The returned units are those of the tag size, therefore the translational components should be scaled with the tag size.
  * The tag coordinates are from (-1,-1) to (1,1), i.e. the tag size has length of 2 units.

      * Optionally, the tag length (in metre) can be passed to return a scaled value.
  * Returns `::Matrix{Float64}`

Related

`homographytopose`
