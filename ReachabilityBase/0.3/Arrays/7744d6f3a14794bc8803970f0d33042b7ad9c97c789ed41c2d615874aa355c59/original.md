```
distance(x::AbstractVector{N}, y::AbstractVector{N}; [p]::Real=N(2)) where {N}
```

Compute the distance between two vectors with respect to the given `p`-norm, computed as

$$
    \|x - y\|_p = \left( \sum_{i=1}^n | x_i - y_i |^p \right)^{1/p}
$$

### Input

  * `x` – vector
  * `y` – vector
  * `p` – (optional, default: `2.0`) the `p`-norm used; `p = 2.0` corresponds to        the usual Euclidean norm

### Output

A scalar representing $‖ x - y ‖_p$.
