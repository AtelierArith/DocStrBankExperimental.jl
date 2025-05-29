```
relative_error(a::Vector{<:Number}, b::Vector{<:Number})
```

ベクトル `a` と `b` の相対誤差を計算します。

# 例

```julia-repl
julia> a = [2, 2]; b = [1, 1]; relative_error(a, b)
0.5
```
