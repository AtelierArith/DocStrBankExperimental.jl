```
coef(path::RegularizationPath, select::SegSelect)
```

Coefficient vector for a selected segment of a regularization path.

# Examples

```julia
coef(path, MinBIC())     # BIC minimizing segment
coef(path, AllSeg())     # Array with entire path's coefficents
```
