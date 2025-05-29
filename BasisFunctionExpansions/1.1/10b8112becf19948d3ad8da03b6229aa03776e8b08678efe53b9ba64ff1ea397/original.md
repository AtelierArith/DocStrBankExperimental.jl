```
y,A = getARregressor(y::AbstractVector,na::Integer)
```

Returns a shortened output signal `y` and a regressor matrix `A` such that the least-squares AR model estimate of order `na` is `y\A`
