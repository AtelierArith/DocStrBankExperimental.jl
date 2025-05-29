```
Gk(k::Int, P1::Vector{T}, P2::Vector{T}, grid::CamiDiff.Grid) where T<:Real
```

$$
k^{th}
$$

-次数の多極子寄与は、中心ポテンシャル内の2つの電子の*交換*放射積分に対する（縮小された）放射波動関数 `P1` と `P2` に対してです。

$$
F^{k}(nl;n^{\prime}l^{\prime})
=\int_{0}^{\infty}U_{F}^{k}(nl;\rho)\left[\tilde{R}_{n^{\prime}l^{\prime}}(\rho)\right]^{2}\rho^{2}d\rho.
$$
