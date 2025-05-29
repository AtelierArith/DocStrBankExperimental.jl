```
ssb_posvel_pN(μ, q)
```

Return the two sums needed to determine the Solar System Barycenter (SSB)

$$
\left\lbrace
\begin{array}{l}
    \sum_i \mu_i^*\mathbf{r}_i = \mathbf{0} \\
    \sum_i \mu_i^*\dot{\mathbf{r}}_i + \dot{\mu}_i^*\mathbf{r}_i = \mathbf{0},
\end{array}
\right.
$$

and the sum of the mass parameters of all the bodies in `q`

$$
\sum_i\mu_i^*, 
$$

where $\mathbf{r}_i$, $\mathbf{v}_i = \dot{\mathbf{r}}_i$ and $\mu_i^*$ are the  barycentric position, barycentric velocity and mass parameter (with relativistic corrections  up to order $1/c^2$) of the `i`-th body. 

See equation (5) of https://doi.org/10.1051/0004-6361:20066607. 

See also [`μ_star_fun`](@ref).

# Arguments

  * `μ`: vector of mass parameters.
  * `q`: vector of positions + velocities + Lunar physical librations + TT-TDB.
