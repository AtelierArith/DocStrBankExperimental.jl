# Extended help

```
translate(P::HPoly, v::AbstractVector; [share]::Bool=false)
```

### Input

  * `share` – (optional, default: `false`) flag for sharing unmodified parts of            the original set representation

### Notes

The normal vectors of the constraints (vector `a` in `a⋅x ≤ b`) are shared with the original constraints if `share == true`.
