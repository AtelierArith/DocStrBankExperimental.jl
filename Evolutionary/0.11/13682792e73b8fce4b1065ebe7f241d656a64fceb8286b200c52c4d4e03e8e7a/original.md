```
LC(d::Real=0.0)
```

Returns a extended line recombination operation, see [Recombination Interface](@ref), which generates offspring `u` and `v` as

  * $u_i = x_i + \alpha (y_i - x_i)$
  * $v_i = y_i + \alpha (x_i - y_i)$

where $\alpha$ is chosen uniform randomly in the interval $[-d;d+1]$.
