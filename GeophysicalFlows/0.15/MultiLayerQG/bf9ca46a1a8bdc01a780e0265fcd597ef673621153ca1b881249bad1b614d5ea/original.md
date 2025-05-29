```
energies(vars, params, grid, sol)
energies(prob)
```

Return the kinetic energy of each fluid layer KE$_1, ...,$ KE$_{n}$, and the potential energy of each fluid interface PE$_{3/2}, ...,$ PE$_{n-1/2}$, where $n$ is the number of layers in the fluid. (When $n=1$, only the kinetic energy is returned.)

The kinetic energy at the $j$-th fluid layer is

$$
𝖪𝖤_j = \frac{H_j}{H} \int \frac1{2} |{\bf ∇} ψ_j|^2 \frac{𝖽x 𝖽y}{L_x L_y} = \frac1{2} \frac{H_j}{H} \sum_{𝐤} |𝐤|² |ψ̂_j|², \ j = 1, ..., n ,
$$

while the potential energy that corresponds to the interface $j+1/2$ (i.e., the interface between the $j$-th and $(j+1)$-th fluid layer) is

$$
𝖯𝖤_{j+1/2} = \int \frac1{2} \frac{f₀^2}{g'_{j+1/2} H} (ψ_j - ψ_{j+1})^2 \frac{𝖽x 𝖽y}{L_x L_y} = \frac1{2} \frac{f₀^2}{g'_{j+1/2} H} \sum_{𝐤} |ψ̂_j - ψ̂_{j+1}|², \ j = 1, ..., n-1 .
$$
