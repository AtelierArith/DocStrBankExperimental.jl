```
mapdomain(::Type{<:AbstractPolynomial}, x::AbstractArray)
mapdomain(::AbstractPolynomial, x::AbstractArray)
```

与えられた x の値は無限大（-∞, ∞）であると仮定し、指定された多項式の定義域に再スケーリングされた値を返します。

# 例

```jldoctest
julia> using Polynomials

julia> x = -10:10
-10:10

julia> extrema(mapdomain(ChebyshevT, x))
(-1.0, 1.0)

```
