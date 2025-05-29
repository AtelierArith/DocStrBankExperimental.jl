```julia
artscene_filter(
    raw_image::Array{T<:AbstractFloat, 3}
) -> Tuple{Array{Float64, 4}, Array{Float64, 3}}

```

# Summary

Process the full artscene filter toolchain on an image.

# Arguments

  * `raw_image::Array{Real, 3}`: the raw RGB image to process with the ARTSCENE filter.

# Method List / Definition Locations

```julia
artscene_filter(raw_image)
```

defined at [`packages/AdaptiveResonance/wgSPV/src/ARTMAP/ARTSCENE.jl:294`](file:///home/terasaki/.julia/packages/AdaptiveResonance/wgSPV/src/ARTMAP/ARTSCENE.jl).
