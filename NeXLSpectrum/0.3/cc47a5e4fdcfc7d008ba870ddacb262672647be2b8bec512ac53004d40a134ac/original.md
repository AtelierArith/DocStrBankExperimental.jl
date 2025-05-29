```
similarity(s1::Spectrum{T}, s2::Spectrum{T}, chs)::Float64 where {T<:Real}
similarity(specs::AbstractArray{Spectrum{T}}, chs)::Vector{Float64}
similarity(specs::AbstractArray{Spectrum}, minE::Float64=100.0)::Vector{Float64}
similarity(specs::AbstractArray{<:Spectrum}, det::Detector, elm::Element)::Vector{Float64}
similarity(specs::AbstractArray{Spectrum{T}}, det::Detector, mat::Material)::Vector{Float64}
```

Returns a vector of similarity metrics which measure how similar the i-th `Spectrum` is to the other spectra. The mean reduced χ² statistic metric is such that if `s1` and `s2` differ by only count statistics  then the metric will be approximately unity.  If `s1` and `s2` vary due to probe current drift, sample  inhomogeneity, surface roughness or other non-count statistics related reasons then the metric will be  larger than one.

The first version covers all the channels between minE and the nominal beam energy. The third and fourth versions considers those channels representing peaks in a spectrum from the `Material` or `Element` on the `Detector`.
