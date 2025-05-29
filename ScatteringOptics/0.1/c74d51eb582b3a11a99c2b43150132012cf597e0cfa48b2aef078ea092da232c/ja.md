```julia
struct ExactScatteringKernel{T, S, N} <: ScatteringOptics.AbstractScatteringKernel{T}
```

散乱モデル `sm <: AbstractScatteringModel` に基づく散乱カーネルのための同志VLBI空モデルで、Psaltis et al. (2018) の正確な公式を使用しています。

デフォルトでは、`T` が指定されていない場合、`T` は `Float64` にデフォルト設定されます。
