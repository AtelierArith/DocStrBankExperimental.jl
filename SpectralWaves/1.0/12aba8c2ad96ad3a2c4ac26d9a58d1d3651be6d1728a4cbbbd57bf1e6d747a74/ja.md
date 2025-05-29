```
convolve_dsp(a::Vector{Ta}, b::Vector{Tb}) where {Ta<:Number, Tb<:Number}
```

ベクトル `a` と `b` の直接畳み込みをDSPパッケージを使用して計算します。

# 例

```julia-repl
julia> a = [1, 2]; b = [1, 1]; convolve(a, b)
3-element Vector{Int64}:
 1
 3
 2
```
