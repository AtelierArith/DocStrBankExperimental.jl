```
overapproximate(Z::AbstractZonotope, ::Type{<:Zonotope}, r::Real)
```

Reduce the order of a zonotopic set.

### Input

  * `Z`        – zonotopic set
  * `Zonotope` – target set type
  * `r`        – desired order

### Output

A new zonotope with `r` generators, if possible.

### Algorithm

This method falls back to `reduce_order` with the default algorithm.
