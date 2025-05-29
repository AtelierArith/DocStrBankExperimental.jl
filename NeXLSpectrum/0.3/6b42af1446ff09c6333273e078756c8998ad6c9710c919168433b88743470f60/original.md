```
NeXLMatrixCorrection.quantify(
    ffr::FitResult,
    iteration::Iteration = Iteration(mc=XPP, fc=ReedFluorescence, cc=Coating);
    strip::AbstractVector{Element} = Element[],
    kro::KRatioOptimizer = SimpleKRatioOptimizer(1.5),
    coating::Union{Nothing, Pair{CharXRay, <:Material}}=nothing
)::IterationResult
```

Facilitates converting `FilterFitResult` or `BasicFitResult` objects into estimates of composition by extracting k-ratios from measured spectra and applying matrix correction algorithms.
