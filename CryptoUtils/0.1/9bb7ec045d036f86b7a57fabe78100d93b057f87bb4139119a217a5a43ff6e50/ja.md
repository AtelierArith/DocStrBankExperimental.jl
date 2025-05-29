```
continued_fraction(a::T, b::T) where T <: Integer
```

有理数 `a/b` の連分数を返します。

# 例

```julia
julia> continued_fraction(31, 73)
6-element Array{Int64,1}:
 0
 2
 2
 1
 4
 2
```
