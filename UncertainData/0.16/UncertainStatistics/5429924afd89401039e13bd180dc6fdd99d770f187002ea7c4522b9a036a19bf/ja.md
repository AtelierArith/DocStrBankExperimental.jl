```
cov(x::AbstractUncertainValue, y::AbstractUncertainValue, n::Int; 
    corrected::Bool = true)
```

2つの不確実な値の間の共分散を計算するには、`x` から `n` サンプルを独立に引き出し、`y` からも `n` サンプルを引き出し、その長さ `n` の引き出しの間の共分散を計算します。
