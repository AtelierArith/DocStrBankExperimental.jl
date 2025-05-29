```
evaluatePCE(x::AbstractVector{<:Real},ξ::AbstractVector{<:Real},α::AbstractVector{<:Real},β::AbstractVector{<:Real})
```

多項式カオス展開の評価

$$
\mathsf{x} = \sum_{i=0}^{L} x_i \phi_i{\xi_j},
$$

ここで `L+1 = length(x)` であり、$x_j$ は $j$ 番目のサンプルで、$j=1,\dots,m$ であり、`m = length(ξ)` です。
