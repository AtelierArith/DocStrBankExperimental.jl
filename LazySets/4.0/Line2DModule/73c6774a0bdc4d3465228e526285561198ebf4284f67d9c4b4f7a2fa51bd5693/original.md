# Extended help

```
translate(L::Line2D, v::AbstractVector; [share]::Bool=false)
```

### Notes

The normal vector of the line (vector `a` in `a⋅x = b`) is shared with the original line if `share == true`.

### Algorithm

A line $a⋅x = b$ is transformed to the line $a⋅x = b + a⋅v$. In other words, we add the dot product $a⋅v$ to $b$.
