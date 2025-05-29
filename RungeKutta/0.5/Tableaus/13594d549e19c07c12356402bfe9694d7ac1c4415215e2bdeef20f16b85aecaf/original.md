Tableau of 3rd order Strong Stability Preserving method with three stages and CFL ≤ 1

```julia
TableauSSPRK3(::Type{T}=Float64) where {T}
```

The constructor takes one optional argument, that is the element type of the tableau.

Reference:

```
Chi-Wang Shu, Stanley Osher.
Efficient implementation of essentially non-oscillatory shock-capturing schemes.
Journal of Computational Physics, Volume 77, Issue 2, Pages 439-471, 1988.
doi: 10.1016/0021-9991(88)90177-5.
Equation (2.18)
```
