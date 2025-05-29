```
resample(x::AbstractArray, rate::Real, h::Vector = resample_filter(rate); dims)
```

配列 `x` を次元 `dims` に沿って再サンプリングします。
