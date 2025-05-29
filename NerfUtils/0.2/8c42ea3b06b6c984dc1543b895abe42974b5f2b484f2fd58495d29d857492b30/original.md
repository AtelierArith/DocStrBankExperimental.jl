Camera intrinsics for projecting from pixel to camera space.

Projection is done as follows: `((x, y) .- principal) ./ focal`. Followed by undistortion if any.

# Arguments:

  * `distortion::Maybe{SVector{4, Float32}}`: If no distortion, then `nothing`.
  * `focal::SVector{2, Float32}`: Focal length in `(fx, fy)` format.
  * `principal::SVector{2, Float32}`: Principal point in `(cx, cy)` format.   Normalized by the `resolution` (in `[0, 1]` range)
  * `resolution::SVector{2, UInt32}`: Resolution in `(width, height)` format.
