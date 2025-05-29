```
coef(path::RegularizationPath; kwargs...)
```

Coefficient vector for a selected segment of a regularization path.

# Examples

```julia
coef(path; select=MinBIC())     # BIC minimizing segment
coef(path; select=AllSeg())     # Array with entire path's coefficents
```
