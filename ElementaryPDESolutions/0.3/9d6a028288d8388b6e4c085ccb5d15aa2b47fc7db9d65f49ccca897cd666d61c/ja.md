```
solve_maxwell(J::NTuple{3,Polynomial{3,T}};ϵ=1,μ=1,ω=1)
```

マクスウェル系を満たす多項式のベクトルのペア `E` と `H` を計算します：

$$
\begin{aligned}
  \mathrm{i}\omega\varepsilon\boldsymbol{E} + \operatorname{rot} \boldsymbol{H} &= \boldsymbol{J}, \qquad &
  -\mathrm{i}\omega\mu\boldsymbol{H} + \operatorname{rot}\boldsymbol{E} &= \boldsymbol{0}, \\
  \varepsilon\operatorname{div}\boldsymbol{E} &= \rho, &
  \mu\operatorname{div}\boldsymbol{H} &= 0,
\end{aligned}
$$

ソースは電荷保存方程式によって制約されています：

$$
\begin{aligned}
  \operatorname{div}\boldsymbol{J} - \mathrm{i}\omega\rho &= 0.
\end{aligned}
$$

ペア `(E, H)` を返します。

# 例

```jldoctest
julia> J = (Polynomial((0,2,1) => 1), Polynomial((0,1,1) => 1), Polynomial((1,0,1) => 1))
(y²z, yz, xz)

julia> E, H = solve_maxwell(J);

julia> E
((-0.0 - 1.0im) + (0.0 + 2.0im)z + (-0.0 - 1.0im)y²z, (-0.0 - 1.0im)yz, (-0.0 - 1.0im) + (-0.0 - 1.0im)xz)

julia> H
(y, 2.0 + z - y², 2.0yz)
```
