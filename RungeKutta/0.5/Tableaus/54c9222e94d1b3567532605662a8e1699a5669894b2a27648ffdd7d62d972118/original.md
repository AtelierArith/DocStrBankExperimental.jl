Radau IIB tableau with s stages

```julia
TableauRadauIIB(::Type{T}, s)
TableauRadauIIB(s) = TableauRadauIIB(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

Coefficients are taken as $a^B = \frac{1}{2} ( a^A + \bar{a}^A )$ where $a^A$ are the coefficients of the Radau IIA method and $\bar{a}^AV are computed such that the symplecticity conditions$b*{i} \bar{a}*{i,j} + \bar{b}*{j} a*{j,i} = b*{i} \bar{b}*{j}$and$b*{i} = \bar{b}*i$hold for all$1 \le i,j \le s``.

Reference:

```
Sun Geng
Construction of high order symplectic Runge-Kutta methods
Journal of Computational Mathematics, Volume 11, Pages 250-260, 1993.
```
