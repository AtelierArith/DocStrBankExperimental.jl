```
variable(var=:x)
variable(::Type{<:AbstractPolynomial}, var=:x)
variable(p::AbstractPolynomial, var=indeterminate(p))
```

指定された多項式基底における単項式 `x` を返します。型が指定されていない場合、デフォルトで [`Polynomial`](@ref) になります。`P(var)` と同等です。

# 例

```jldoctest
julia> using Polynomials

julia> x = variable()
Polynomial(x)

julia> p = 100 + 24x - 3x^2
Polynomial(100 + 24*x - 3*x^2)

julia> roots((x - 3) * (x + 2))
2-element Vector{Float64}:
 -2.0
  3.0
```
