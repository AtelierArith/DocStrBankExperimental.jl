```
sharpe(R::TSFrame, Rf::Number=0)
```

`資産のリターン`から`シャープレシオ`を計算します。出力は`NamedArray`です。

# 引数:

  * `R::TSFrame`: 資産リターンのTSFrameオブジェクトの列
  * `Rf::Number=0`: 無リスク金利

# 例

```julia
julia> sharpe = sharpe(returns)
4-element Named Vector{Float64}
シャープレシオ (Rf=0)  │
─────────────────────┼─────────
TSLA                 │ 0.288602
NFLX                 │ 0.170242
MSFT                 │ 0.606824
```
