```
IC(d::Real=0.0)
```

Returns an extended intermediate recombination operation, see [Recombination Interface](@ref), which generates offspring `u` and `v` as

  * $u_i = x_i + \alpha_i (y_i - x_i)$
  * $v_i = y_i + \alpha_i (x_i - y_i)$

where $\alpha_i$ is chosen uniform randomly in the interval $[-d;d+1]$.
