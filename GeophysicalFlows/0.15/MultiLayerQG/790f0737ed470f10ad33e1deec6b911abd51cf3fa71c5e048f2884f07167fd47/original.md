```
fluxes(vars, params, grid, sol)
fluxes(prob)
```

Return the lateral eddy fluxes within each fluid layer, lateralfluxes$_1,...,$lateralfluxes$_n$ and also the vertical eddy fluxes at each fluid interface, verticalfluxes$_{3/2},...,$verticalfluxes$_{n-1/2}$, where $n$ is the total number of layers in the fluid. (When $n=1$, only the lateral fluxes are returned.)

The lateral eddy fluxes within the $j$-th fluid layer are

$$
\textrm{lateralfluxes}_j = \frac{H_j}{H} \int U_j v_j ∂_y u_j
\frac{𝖽x 𝖽y}{L_x L_y} , \  j = 1, ..., n ,
$$

while the vertical eddy fluxes at the $j+1/2$-th fluid interface (i.e., interface between the $j$-th and $(j+1)$-th fluid layer) are

$$
\textrm{verticalfluxes}_{j+1/2} = \int \frac{f₀²}{g'_{j+1/2} H} (U_j - U_{j+1}) \,
v_{j+1} ψ_{j} \frac{𝖽x 𝖽y}{L_x L_y} , \ j = 1, ..., n-1.
$$
