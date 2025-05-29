```
fluxes(vars, params, grid, sol)
fluxes(prob)
```

流体層内の横方向渦フラックスを返します。lateralfluxes$_1,...,$lateralfluxes$_n$ と、各流体インターフェースでの縦方向渦フラックス、verticalfluxes$_{3/2},...,$verticalfluxes$_{n-1/2}$ も返します。ここで、$n$ は流体の層の総数です。（$n=1$ の場合、横方向フラックスのみが返されます。）

$$
j
$$

-th 流体層内の横方向渦フラックスは次のように表されます。

$$
\textrm{lateralfluxes}_j = \frac{H_j}{H} \int U_j v_j ∂_y u_j
\frac{𝖽x 𝖽y}{L_x L_y} , \  j = 1, ..., n ,
$$

一方、$j+1/2$-th 流体インターフェース（すなわち、$j$-th と $(j+1)$-th 流体層の間のインターフェース）での縦方向渦フラックスは次のように表されます。

$$
\textrm{verticalfluxes}_{j+1/2} = \int \frac{f₀²}{g'_{j+1/2} H} (U_j - U_{j+1}) \,
v_{j+1} ψ_{j} \frac{𝖽x 𝖽y}{L_x L_y} , \ j = 1, ..., n-1.
$$
