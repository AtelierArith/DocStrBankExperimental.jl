```
degrees(f::AbstractVector{Expression}, vars = variables(f); expanded = false)
```

Compute the degrees of the expressions `f` in `vars`. Unless `expanded` is `true` the expressions are first expanded.
