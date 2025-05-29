Lobatto IIIG tableau with s stages

```julia
TableauLobattoIIIG(::Type{T}, s)
TableauLobattoIIIG(s) = TableauLobattoIIIG(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

Symplectizied algorithm for [`TableauLobattoIIIF`](@ref)

Coefficients are taken as $a^G = \frac{1}{2} ( a^F + \bar{a}^F )$ where the coefficients $\bar{a}^F$ are computed such that the symplecticity conditions $b_{i} \bar{a}_{i,j} + \bar{b}_{j} a_{j,i} = b_{i} \bar{b}_{j}$ and $b_{i} = \bar{b}_i$ hold for all $1 \le i,j \le s$.
