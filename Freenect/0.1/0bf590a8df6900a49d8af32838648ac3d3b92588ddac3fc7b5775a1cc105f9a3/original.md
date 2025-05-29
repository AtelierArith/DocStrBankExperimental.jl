```julia
sync_get_pointcloud(
    index::Integer
) -> Tuple{Array{Float64, 3}, Int64}

```

Helper for getting a pointcloud from the camera at `index`.

The resulting point cloud is relative to the camera, with X forward, Y left, and Z up.

This function uses a fixed homography matrix - you may have better results for your own hardware by calibrating your Kinect.
