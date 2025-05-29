```
ot_dist(x::Union{PyObject, Array{Float64}}, y::Union{PyObject, Array{Float64}}, order::Union{Int64, PyObject}=2)
```

Computes the distance function with norm `order`. `dist` returns a $n\times m$ matrix, where $x\in \mathbb{R}^{n\times d}$ and $y\in \mathbb{R}^{m\times d}$, and the return $M\in \mathbb{R}^{n\times m}$

$$
M_{ij} = ||x_i - y_j||_{o}
$$
