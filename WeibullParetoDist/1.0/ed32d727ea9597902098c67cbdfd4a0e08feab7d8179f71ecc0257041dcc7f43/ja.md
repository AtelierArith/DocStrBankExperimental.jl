```
truncated(d0::WeibullPareto; [lower::Real], [upper:real])
truncated(d0::WeibullPareto, lower::Real, upper::Real)
```

```julia
truncated(d0; lower=l)     # 左側切断 [l, Inf) の区間
truncated(d0; upper=u)     # 右側切断 [0, u) の区間
truncated(d0; lower=l, upper=u)     # 両側切断 [l, u] の区間
```
