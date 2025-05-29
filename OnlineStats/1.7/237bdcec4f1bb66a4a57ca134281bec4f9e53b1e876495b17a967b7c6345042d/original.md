```
FitLogNormal()
```

Online parameter estimate of a LogNormal distribution (MLE).

# Example

```
o = fit!(FitLogNormal(), exp.(randn(10^5)))
```
