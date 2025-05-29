```
NeXLMatrixCorrection.quantify(
    spec::Union{Spectrum,AbstractVector{<:Spectrum}},
    ffp::FilterFitPacket;
    strip::AbstractVector{Element} = Element[],
    iteration::Iteration = Iteration(mc=XPP, fc=ReedFluorescence, cc=Coating),
    kro::KRatioOptimizer = SimpleKRatioOptimizer(1.5),
    coating::Union{Nothing, Pair{CharXRay, <:Material}}=nothing
)::IterationResult
```

Failitates quantifying spectra.  First filter fits and then matrix corrects.
