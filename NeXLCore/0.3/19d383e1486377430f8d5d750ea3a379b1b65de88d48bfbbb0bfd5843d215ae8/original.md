`KRatios` represents the hyper-spectral equivalent of the KRatio type.  Each pixel in the `KRatios` object must be characterized by the same unknown and standard properties, the same X-ray lines and the other properties.

Methods:

```
> Base.getindex(krs::KRatios, idx::Int...)
> Base.getindex(krs::KRatios, ci::CartesianIndex)
> Base.size(krs::KRatios, [idx::Int])
> Base.CartesianIndices(krs::KRatios)
> normalizek(krs::AbstractVector{<:KRatios}; norm::Float32=1.0f)::Vector{KRatios}
> normalizek(krs::AbstractVector{KRatio}; norm::Float32=1.0f)::Vector{KRatio}
> brightest(krs::Union{KRatios, KRatio})
> colorize(krs::AbstractVector{<:KRatios}, red::Element, green::Element, blue::Element, normalize=:All[|:Each])
> colorize(krs::AbstractVector{<:KRatios}, elms::AbstractVector{Element}, normalize=:All)
> Base.getindex(krs::AbstractVector{<:KRatios}, elm::Element) # Gray scale image
> Base.getindex(krs::AbstractVector{<:KRatios}, red::Element, green::Element)  # Red-green image
> Base.getindex(krs::AbstractVector{<:KRatios}, red::Element, green::Element, blue::Element) # RGB image
```
