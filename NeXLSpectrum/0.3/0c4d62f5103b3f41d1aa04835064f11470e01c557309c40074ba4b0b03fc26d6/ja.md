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

スペクトルの定量化を行います。最初にフィルターフィットを行い、その後マトリックス補正を行います。
