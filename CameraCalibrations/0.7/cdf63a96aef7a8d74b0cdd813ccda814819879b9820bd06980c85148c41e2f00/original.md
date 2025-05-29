```
Calibration(files, n_corners, checker_size, extrinsic_index)
```

Build a calibration object. `files` are the image files of the checkerboard. `n_corners` is a tuple of the number of corners in each of the sides of the checkerboard. `checker_size` is the physical size of the checker (e.g. in cm). `with_distortion` controls if radial lens distortion is included in the model or not.
