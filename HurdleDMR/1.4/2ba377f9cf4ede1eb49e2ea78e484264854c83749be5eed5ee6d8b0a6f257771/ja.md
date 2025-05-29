```
coef(m::HDMRPaths, select::SegSelect=MinAICc())
```

HDMRでフィットしたすべてまたは選択された係数行列を返します。

# 例:

```julia
  m = fit(HDMRPaths,covars,counts)
  coefspos, coefszero = coef(m, MinCVKfold{MinCVmse}(5))
```
