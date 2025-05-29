Mishchenko et al. (2002) の Eq. (5.42) – Eq. (5.44) によれば、Mie 粒子の T-行列は次のように書くことができます：

$$
\begin{array}{l}
T_{m n m^{\prime} n^{\prime}}^{12}(P) \equiv 0, \quad T_{m n m^{\prime} n^{\prime}}^{21}(P) \equiv 0, \\
T_{m n m^{\prime} n^{\prime}}^{11}(P)=-\delta_{m m^{\prime}} \delta_{n n^{\prime}} b_n, \\
T_{m n m^{\prime} n^{\prime}}^{22}(P)=-\delta_{m m^{\prime}} \delta_{n n^{\prime}} a_n .
\end{array}
$$

```
MieTransitionMatrix{CT, N}(x::Real, m::Number)
```

均一な球の Mie 係数から T-行列を生成します。

```
MieTransitionMatrix{CT, N}(x_core::Real, x_mantle::Real, m_core::Number, m_mantle::Number)
```

被覆された球の Mie 係数から T-行列を生成します。

この構造体は Mie 粒子の T-行列 API を提供します。
