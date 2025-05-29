```
bet(
    mag::AbstractArray{<:Real, 3},
    vsz::NTuple{3, Real},
    betargs::AbstractString = "-m -n -f 0.5"
) -> Array{Bool, 3}
```

Interface to FSL's bet.

### Arguments

  * `mag::AbstractArray{<:Real, 3}`: magnitude image
  * `vsz::NTuple{3, Real}`: voxel size
  * `betargs::AbstractString = "-m -n -f 0.5"`: bet options

### Returns

  * `Array{Bool, 3}`: binary brain mask
