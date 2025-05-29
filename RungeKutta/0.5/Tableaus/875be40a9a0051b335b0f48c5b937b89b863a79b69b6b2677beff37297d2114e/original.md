Radau IB tableau with s stages

```julia
TableauRadauIB(::Type{T}, s)
TableauRadauIB(s) = TableauRadauIB(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

Coefficients are taken as $a^B = \frac{1}{2} ( a^A + \bar{a}^A )$ where $a^A$ are the coefficients of the Radau IA method and $\bar{a}^A$ are computed such that the symplecticity conditions $b_{i} \bar{a}_{i,j} + \bar{b}_{j} a_{j,i} = b_{i} \bar{b}_{j}$ and $b_{i} = \bar{b}_i$ hold for all $1 \le i,j \le s$.

Reference:

```
Sun Geng
Construction of high order symplectic Runge-Kutta methods
Journal of Computational Mathematics, Volume 11, Pages 250-260, 1993.
```
