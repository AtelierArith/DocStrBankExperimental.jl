Tableau of 2rd order Strong Stability Preserving method with two stages and CFL ≤ 1

```julia
TableauSSPRK2(::Type{T}=Float64) where {T}
```

The constructor takes one optional argument, that is the element type of the tableau.

This is the same tableau as [`TableauHeun2`](@ref).

Reference:

```
Chi-Wang Shu, Stanley Osher.
Efficient implementation of essentially non-oscillatory shock-capturing schemes.
Journal of Computational Physics, Volume 77, Issue 2, Pages 439-471, 1988.
doi: 10.1016/0021-9991(88)90177-5.
Equation (2.16)
```
