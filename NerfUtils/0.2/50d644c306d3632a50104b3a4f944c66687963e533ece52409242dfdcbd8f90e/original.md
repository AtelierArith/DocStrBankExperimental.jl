```
Camera(projection, intrinsics::CameraIntrinsics)
```

Camera maintains original focal length, since the model was trained on a specific value of it, thus we want to preserve the original aspect.

# Arguments:

  * `projection::MMatrix{3, 4, Float32}`: Camera-to-world projection.
  * `intrinsics::CameraIntrinsics`: Camera intrinsics.
  * `original_focal::SVector{2, Float32}`: Original focal length.   Used during camera resizing to preserve original focal length aspect ratio.
  * `original_resolution::SVector{2, UInt32}`: Original resolution.   Used during camera resizing to compute scale value   to multiply with `original_focal`.
