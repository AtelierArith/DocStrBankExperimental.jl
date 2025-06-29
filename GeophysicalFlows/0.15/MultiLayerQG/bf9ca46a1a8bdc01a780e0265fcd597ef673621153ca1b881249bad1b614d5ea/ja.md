```
energies(vars, params, grid, sol)
energies(prob)
```

各流体層の運動エネルギー KE$_1, ...,$ KE$_{n}$ と、各流体界面のポテンシャルエネルギー PE$_{3/2}, ...,$ PE$_{n-1/2}$ を返します。ここで、$n$ は流体の層の数です。（$n=1$ の場合、運動エネルギーのみが返されます。）

$$
j
$$

-th 流体層における運動エネルギーは次のように表されます。

$$
𝖪𝖤_j = \frac{H_j}{H} \int \frac1{2} |{\bf ∇} ψ_j|^2 \frac{𝖽x 𝖽y}{L_x L_y} = \frac1{2} \frac{H_j}{H} \sum_{𝐤} |𝐤|² |ψ̂_j|², \ j = 1, ..., n ,
$$

一方、インターフェース $j+1/2$（すなわち、$j$-th と $(j+1)$-th 流体層の間のインターフェース）に対応するポテンシャルエネルギーは次のように表されます。

$$
𝖯𝖤_{j+1/2} = \int \frac1{2} \frac{f₀^2}{g'_{j+1/2} H} (ψ_j - ψ_{j+1})^2 \frac{𝖽x 𝖽y}{L_x L_y} = \frac1{2} \frac{f₀^2}{g'_{j+1/2} H} \sum_{𝐤} |ψ̂_j - ψ̂_{j+1}|², \ j = 1, ..., n-1 .
$$
