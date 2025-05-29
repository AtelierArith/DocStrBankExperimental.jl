```
e = prediction_error(sys::AbstractStateSpace, d::AbstractIdData, args...; kwargs...)
```

予測誤差 `d.y - predict(sys, d, ...` を返します。
