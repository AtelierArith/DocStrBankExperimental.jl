```
fromroots(::AbstractVector{<:Number}; var=:x)
fromroots(::Type{<:AbstractPolynomial}, ::AbstractVector{<:Number}; var=:x)
```

与えられた根から指定された型の多項式を構築します。型が指定されていない場合、デフォルトは `Polynomial` です。

# 例

```jldoctest
julia> using Polynomials

julia> r = [3, 2]; # (x - 3)(x - 2)

julia> fromroots(r)
Polynomial(6 - 5*x + x^2)
```
