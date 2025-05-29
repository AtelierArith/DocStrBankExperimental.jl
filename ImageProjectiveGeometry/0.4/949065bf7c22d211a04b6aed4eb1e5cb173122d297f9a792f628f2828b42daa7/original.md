camera2projmatrix - Generate a camera projection matrix from a Camera structure

```
Usage:     P = camera2projmatrix(C)

Argument:  C - Camera structure

Returns:   P - 3x4 camera projection matrix that maps homogeneous 3D world
           coordinates to homogeneous image coordinates.
```

Function takes a camera structure and returns its equivalent projection matrix ignoring lens distortion parameters etc.

See also: Camera(), projmatrix2camera(), cameraproject()
