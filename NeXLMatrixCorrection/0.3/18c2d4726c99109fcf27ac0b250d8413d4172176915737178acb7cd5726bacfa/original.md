```
quantify(
    name::Union{String, Label},
    measured::Vector{KRatio}, 
    iteration::Iteration = Iteration(mc=XPP, fc=ReedFluorescence, cc=Coating);
    maxIter::Int = 100, 
    estComp::Union{Nothing,Material}=nothing, 
    coating::Union{Nothing, Pair{CharXRay, <:Material}}=nothing
)::IterationResult

quantify(
    measured::AbstractVector{KRatios{T}},
    iteration::Iteration = Iteration(mc=XPP, fc=NullFluorescence, cc=NullCoating);
    kro::KRatioOptimizer = SimpleKRatioOptimizer(1.5),
    maxIter::Int = 100, 
    estComp::Union{Nothing,Material}=nothing, 
    coating::Union{Nothing, Pair{CharXRay, Material}}=nothing
)
```

Perform the iteration procedurer as described in `iter` using the `measured` k-ratios to produce the best estimate `Material` in an `IterationResult` object.  The third form makes it easier to quantify the k-ratios from filter fit spectra.  `estComp` is an optional first estimate of the composition.  This can be a useful optimization when quantifying many similar k-ratios (like, for example, points on a  hyper-spectrum.)

`coating` defines a CharXRay not present in the sample that is used to estimate the thickness of the coating layer (of the paired `Material`).
