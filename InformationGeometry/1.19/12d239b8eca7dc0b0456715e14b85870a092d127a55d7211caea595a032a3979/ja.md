```
PropagateUncertainty(F::Function, woundX::AbstractVector, sol::AbstractODESolution, mle::AbstractVector; samples::Int=100, plot::Bool=isloaded(:Plots), kwargs...)
```

関数 `F` を通じて不確実性を伝播させます。
