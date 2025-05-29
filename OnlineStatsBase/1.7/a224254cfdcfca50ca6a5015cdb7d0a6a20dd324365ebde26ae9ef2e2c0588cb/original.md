```
Mean(T = Float64; weight=EqualWeight())
```

Track a univariate mean, stored as type `T`.

# Example

```
@time fit!(Mean(), randn(10^6))
```
