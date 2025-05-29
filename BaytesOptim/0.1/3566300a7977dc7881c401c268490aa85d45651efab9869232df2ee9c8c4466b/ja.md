```julia
struct Optimizer{M<:BaytesOptim.OptimKernel, N<:BaytesOptim.OptimTune} <: BaytesCore.AbstractAlgorithm
```

提案ステップの情報を格納します。

# フィールド

  * `kernel::BaytesOptim.OptimKernel`: オプティマイザー
  * `tune::BaytesOptim.OptimTune`: カーネルのチューニング設定。
