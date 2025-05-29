```
LeonenkoProzantoSavani <: DifferentialInfoEstimator
LeonenkoProzantoSavani(definition = Shannon(); k = 1, w = 0)
```

`LeonenkoProzantoSavani`推定器[LeonenkoProzantoSavani2008](@cite)は、指定された`definition`の`base`で対数を用いて、多次元[`StateSpaceSet`](@ref)の[`Shannon`](@ref)、[`Renyi`](@ref)、または[`Tsallis`](@ref)の微分[`information`](@ref)を計算します。

## 説明

この推定器は`k`-最近傍探索を使用します。`w`はタイラーウィンドウで、隣接点探索中に時間的隣接点が除外されるかどうかを決定します（デフォルトは`0`で、これは隣接点を探索する際に点自体のみが除外されることを意味します）。

詳細については、[LeonenkoProzantoSavani2008](@citet)を参照してください。
