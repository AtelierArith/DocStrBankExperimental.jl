```
getdiffeps()
setdiffeps(b::Real)
```

Two quantities are tested for equality if the absolute value of their difference is smaller than `getdiffoeps()`. Default value: $10^{-12}$.
