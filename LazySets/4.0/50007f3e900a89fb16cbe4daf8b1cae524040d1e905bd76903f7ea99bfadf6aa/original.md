# Extended help

```
σ(d::AbstractVector, H::AbstractHyperrectangle)
```

### Notes

If the direction vector is zero in dimension $i$, the result will have the center's coordinate in that dimension. For instance, for the two-dimensional infinity-norm ball, if the direction points to the right, the result is the vector `[1, 0]` in the middle of the right-hand facet.

If the direction has norm zero, the result can be any point in `H`. The default implementation returns the center of `H`.
