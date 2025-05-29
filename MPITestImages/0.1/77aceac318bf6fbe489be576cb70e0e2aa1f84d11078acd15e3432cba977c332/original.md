```julia
jaszczak_phantom(
    radiusSpheres,
    derenzoImage,
    height,
    distanceSpheresToRods,
    heightRods
)

```

Function to generate the Jaszczak Phantom. It is necessary to generate a Derenzo phantom first as it is part of the 3D body to generate.

# Arguments

  * `radiusSpheres::Vector{Int64}`: Vector with length 6 giving the radius of each sphere of the phantom.
  * `derenzoImage::Matrix{Float64}`: The Derenzo phantom which is part of the Jaszczak Phantom.

The dimensions of this image dictates the depth and width of the resulting phantom.

  * `height::Int64`: The height of the phantom.
  * `distanceSpheresToRods::Int64`: The distance between the spheres and the beginning of the rods.
  * `heightRods::Int64`: The height of the rods (The Derenzo phantom part).

# Returns

  * `Array{Float64, 3}`: The three dimensional phantom.
