```
showbasis(α::Vector{<:Real},β::Vector{<:Real};sym::String,digits::Integer)
```

Show all basis polynomials given the recurrence coefficients `α`, `β`. The keyword `sym` sets the name of the variable, and `digits` controls the number of shown digits.

```jldoctest
julia> using PolyChaos

julia> α, β = rm_hermite(5);

julia> showbasis(α, β)
1
x
x^2 - 0.5
x^3 - 1.5x
x^4 - 3.0x^2 + 0.75
x^5 - 5.0x^3 + 3.75x
```

Tailored to types from `PolyChaos.jl`

```
showbasis(op::AbstractOrthoPoly;sym::String,digits::Integer)
```

Show all basis polynomials of an `AbstractOrthoPoly`.

```jldoctest
julia> using PolyChaos

julia> op = LegendreOrthoPoly(4);

julia> showbasis(op)
1
x
x^2 - 0.33
x^3 - 0.6x
x^4 - 0.86x^2 + 0.09
```
