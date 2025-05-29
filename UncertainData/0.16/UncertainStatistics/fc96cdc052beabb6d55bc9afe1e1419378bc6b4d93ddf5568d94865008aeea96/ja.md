```
cor(x::AbstractUncertainValue, y::AbstractUncertainValue, n::Int)
```

2つの不確実な値の間のピアソン相関を計算します。`x`から`n`サンプル、`y`から`n`サンプルを独立に引き出し、その長さ`n`の引き出しの間のピアソン相関を計算します。
