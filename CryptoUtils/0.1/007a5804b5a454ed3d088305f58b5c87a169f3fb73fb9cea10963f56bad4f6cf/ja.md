```
convergents(a::T, b::T) where T <: Integer
```

有理数 `a/b` の収束値を返します。

# 例

```julia
julia> convergents(31, 73)
6-element Array{Rational,1}:
  0//1
  1//2
  2//5
  3//7
 14//33
 31//73
```
