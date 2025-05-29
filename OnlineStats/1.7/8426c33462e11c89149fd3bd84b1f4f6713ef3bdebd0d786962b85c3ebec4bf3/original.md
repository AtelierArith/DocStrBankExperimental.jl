```
AutoCov(b, T = Float64; weight=EqualWeight())
```

Calculate the auto-covariance/correlation for lags 0 to `b` for a data stream of type `T`.

# Example

```
y = cumsum(randn(100))
o = AutoCov(5)
fit!(o, y)
autocov(o)
autocor(o)
```
