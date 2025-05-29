```
Transfer(domain)
Transfer([g₁, g₂, ..., gₙ])
```

Transfer variables `var₁`, `var₂`, ..., `varₙ` from source domain to target `domain`. Alternatively, transfer variables to geometries `g₁`, `g₂`, ..., `gₙ`.

# Examples

```julia
Transfer(CartesianGrid(10, 10))
Transfer(rand(Point, 100))
```
