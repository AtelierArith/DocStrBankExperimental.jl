```
value(q)
value(q, pos)
```

Get the value of the varying quantity `q` at the given position `pos`. `pos` may be specified as a `(x, y, z)` tuple, a `(x, z)` tuple, or a `z` value.

# Examples

```julia
value(q)             # get value of a constant quantity
value(q, -10)        # get value of a depth-dependent quantity at z=-10
value(q, (1000,-10)) # get value of a position-dependent quantity at x=1000, z=-10
value(q, (0,0,-10))  # get value of a position-dependent quantity at (0,0,-10)
```
