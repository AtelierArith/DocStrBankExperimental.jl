```
NeXLMatrixCorrection.quantify(
    ffr::FitResult,
    iteration::Iteration = Iteration(mc=XPP, fc=ReedFluorescence, cc=Coating);
    strip::AbstractVector{Element} = Element[],
    kro::KRatioOptimizer = SimpleKRatioOptimizer(1.5),
    coating::Union{Nothing, Pair{CharXRay, <:Material}}=nothing
)::IterationResult
```

`FilterFitResult`または`BasicFitResult`オブジェクトを、測定されたスペクトルからk比を抽出し、マトリックス補正アルゴリズムを適用することによって組成の推定に変換することを容易にします。
