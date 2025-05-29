```
KRatio(
    xray::Vector{CharXRay},
    unkProps::Dict{Symbol,<:Any},
    stdProps::Dict{Symbol,<:Any},
    standard::Material,
    kratio::AbstractFloat,
)
```

The k-ratio is the ratio of two similar intensity measurements - one on  a material of unknown composition and one on a standard with known  composition. Each measurement has properties like :BeamEnergy (req),  :TakeOffAngle (req), :Coating (opt) that characterize the measurement.   A minimal set of properties includes:

Properties: (These `Symbol`s are intentionally the same used in NeXLSpectrum)

```
:BeamEnergy incident beam energy in eV
:TakeOffAngle in radians
:Coating A NeXLCore.Film object or Film[] detailing a conductive coating
```

Some algorithms may require additional properties.

k-ratios are associated with characteristic X-rays (`CharXRay`) from a single element. WDS k-ratios are typically associated with a single `CharXRay` while EDS measurements may be associated with many `CharXRay` that are similar in energy. k-ratios are always relative to another material.  Usually the composition of this `Material` is well-known.  However, when a k-ratio is restandardized, it is possible for the intermediate material to be less well-known.

Methods:

```
> element(kr)
> xrays(kr)
> standard(kr)
> elms(KRatioBase[...])
> NeXLUncertainties.value(kr::KRatio)
> NeXLUncertainties.σ(kr::KRatio)
> nonnegk(kr::KRatio)
> Statistics.mean(krs::AbstractVector{KRatio})::UncertainValue
> Base.getindex(krs::AbstractVector{KRatio}, cxr::CharXRay)
> strip(krs::AbstractVector{KRatio}, els::Element...)::Vector{KRatio}
> using DataFrames
> DataFrame(krs::AbstractVector{KRatio})::DataFrame
```
