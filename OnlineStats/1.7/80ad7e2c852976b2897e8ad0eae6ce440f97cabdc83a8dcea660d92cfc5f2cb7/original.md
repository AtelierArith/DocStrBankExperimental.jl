```
FitMvNormal(d)
```

Online parameter estimate of a `d`-dimensional MvNormal distribution (MLE).

# Example

```
y = randn(100, 2)
o = fit!(FitMvNormal(2), eachrow(y))
```
