```
convolution_power(a::Vector{<:Number}, n::Integer)
```

ベクトル `a` の畳み込み `n` 乗を計算します。

# 例

```julia-repl
julia> a = [1, 2, 3]; convolution_power(a, 3)
7-element Vector{Int64}:
  1
  6
 21
 44
 63
 54
 27
```
