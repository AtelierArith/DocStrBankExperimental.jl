```
node_densities(cell_positions::AbstractVector{T}; smooth_boundary=true) where {T<:Number}
```

Compute the cell densities from the cell positions, assigning a density to each node. If  `smooth_boundary` is true, then 

$$
q_i(t) = \begin{cases} \dfrac{2}{x_2(t)-x_1(t)} - \dfrac{2}{x_3(t)-x_1(t)} & i=1, \\[6pt]
\dfrac{2}{x_{i+1}(t)-x_{i-1}(t)} & i=2,\ldots,n-1, \\[6pt]
\dfrac{2}{x_n(t) - x_{n-1}(t)} - \dfrac{2}{x_n(t)-x_{n-2}(t)} & i=n. \end{cases}
$$

Otherwise,

$$
q_i(t) = \begin{cases} \dfrac{1}{x_2(t)-x_1(t)} & i=1, \\[6pt]
\dfrac{2}{x_{i+1}(t)-x_{i-1}(t)} & i=2,\ldots,n-1, \\[6pt]
\dfrac{1}{x_n(t) - x_{n-1}(t)} & i=n. \end{cases}
$$

If you want estimates of the densities for each cell rather than at each node, see [`cell_densities`](@ref).
