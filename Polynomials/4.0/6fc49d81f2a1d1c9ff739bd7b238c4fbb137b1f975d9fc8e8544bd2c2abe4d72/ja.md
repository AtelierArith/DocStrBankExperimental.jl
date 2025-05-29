```
fromroots(::AbstractMatrix{<:Number}; var=:x)
fromroots(::Type{<:AbstractPolynomial}, ::AbstractMatrix{<:Number}; var=:x)
```

与えられた行列の固有値を根として使用して、指定された型の多項式を構築します。型が指定されていない場合、デフォルトは `Polynomial` です。

# 例

```jldoctest
julia> using Polynomials

julia> A = [1 2; 3 4]; # (x - 5.37228)(x + 0.37228)

julia> fromroots(A)
Polynomial(-1.9999999999999998 - 5.0*x + 1.0*x^2)
```
