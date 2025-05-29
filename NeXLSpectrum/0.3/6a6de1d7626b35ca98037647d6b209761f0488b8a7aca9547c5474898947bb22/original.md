```
buildfilter(
    [ ::Type{T} = Float64],
    ty::Type{<:TopHatFilterType},
    det::Detector,
    a::AbstractFloat = 1.0, # Top
    b::AbstractFloat = 2.0,  # Base
)
buildfilter(::Type{T}, det::Detector, a::AbstractFloat = 1.0, b::AbstractFloat = 2.0) where { T<:AbstractFloat }
buildfilter(det::Detector, a::AbstractFloat = 1.0, b::AbstractFloat = 2.0)::TopHatFilter{Float64}
buildfilter(ty::Type{<:TopHatFilterType}, det::Detector, a::AbstractFloat = 1.0, b::AbstractFloat = 2.0)::TopHatFilter{Float64}
```

Build a top-hat filter for the specified detector with the specified top and base parameters.  The default element type is `Float64` and the default shape model (`TopHatFilterType`) is `VariableWidthFilter`.
