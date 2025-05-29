```
selectmodel(path::RegularizationPath, select::SegSelect)
```

Returns a LinearModel or GeneralizedLinearModel representing the selected segment of a regularization path.

# Examples

```julia
selectmodel(path, MinBIC())            # BIC minimizing model
selectmodel(path, MinCVmse(path, 5))   # 5-fold CV mse minimizing model
```
