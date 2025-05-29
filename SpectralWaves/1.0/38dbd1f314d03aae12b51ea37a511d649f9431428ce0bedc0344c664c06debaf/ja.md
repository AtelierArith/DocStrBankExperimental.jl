```
absolute_error(a::Vector{<:Number}, b::Vector{<:Number})
```

ベクトル `a` と `b` の間の絶対誤差を計算します。

# 例

```julia-repl
julia> a = [1, 2]; b = [1, 1]; absolute_error(a, b)
1.0
```
