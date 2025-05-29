```
Fk(k::Int, P1::Vector{T}, P2::Vector{T}, grid::CamiDiff.Grid) where T<:Real
```

$$
k^{th}
$$

-次数の多極子寄与は、中心ポテンシャル場における2つの電子の（縮小された）ラジアル波動関数 `P1` と `P2` に対する*直接*ラジアル積分です（軌道 $nl$ と $n^{\prime}l^{\prime}$ において）。

$$
F^{k}(nl;n^{\prime}l^{\prime})
=\int_{0}^{\infty}U_{F}^{k}(nl;\rho)\left[\tilde{R}_{n^{\prime}l^{\prime}}(\rho)\right]^{2}\rho^{2}d\rho
=\int_{0}^{\infty}U_{F}^{k}(n^{\prime}l^{\prime};\rho)\left[\tilde{R}_{nl}(\rho)\right]^{2}\rho^{2}d\rho.
$$

```
Fk(k::Int, P::Vector{T}, grid::CamiDiff.Grid) where T<:Real
```

$$
k^{th}
$$

-次数の寄与は、中心ポテンシャルにおける2つの*同等の* $nl$ 電子の（縮小された）ラジアル波動関数 `P` に対する*直接*ラジアル積分です。

$$
F^{k}(nl)
=\int_{0}^{\infty}U_{F}^{k}(nl;\rho)\left[\tilde{R}_{nl}(\rho)\right]^{2}\rho^{2}d\rho.
$$
