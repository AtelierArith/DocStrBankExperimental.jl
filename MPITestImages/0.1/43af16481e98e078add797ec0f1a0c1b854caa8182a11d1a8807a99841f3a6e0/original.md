```julia
derenzo_image(
    diameter,
    pointSizePerSextant,
    gapBetweenSextants;
    distanceBetweenPoints,
    arrowShape
)

```

Function to generate Derenzo Phantom. This is done by specifying the diameter of the phantom and the size in pixel and  for each sextant of the phantom. The algorithm tries to fill the radius with as many dots as possible.

# Arguments

  * `diameter::Int64`: Diameter in pixel of the phantom.
  * `pointSizePerSextant::Vector{Integer}`: Size for the points in each sextant. Should atleast be of length 6.
  * `gapBetweenSextants::Union{Int64, Vector{Int64}}`: Gap between the center of the phantom and the sextants.

# Optional Arguments

`distanceBetweenPoints::Union{Int64, Vector{Int64}}=-1`: The ctc distance of the holes.  `arrowShape::Bool=false`: If true the last row of each sextant will have another row of one less hole if it fits.

# Returns

  * `image::Matrix{Float64}`: The resulting Derenzo phantom.

# Examples

This call generates a phantom similar to QRMs Mini Derenzo Phantom:

```
derenzo = derenzo_image(600, 
	Int.(round.([0.6*500, 0.8*500, 1.0*500, 1.2*500, 1.5*500, 2.0*500]./29)), 
	30,
	distanceBetweenPoints=Int.(round.([1.2*500, 1.6*500, 2.0*500, 2.4*500, 3.0*500, 4.0*500]./29)),
	arrowShape=true)
```
