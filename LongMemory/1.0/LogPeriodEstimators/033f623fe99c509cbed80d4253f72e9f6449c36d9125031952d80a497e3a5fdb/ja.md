```
periodogram(x::Array)
```

時系列 `x` の周期ogramを高速フーリエ変換を使用して計算します。

# 引数

  * `x::Vector`: 時系列

# 出力

  * `I_w::Vector`: 周期ogram
  * `w::Vector`: フーリエ周波数

# 例

```julia-repl
julia> periodogram(randn(100,1))
```
