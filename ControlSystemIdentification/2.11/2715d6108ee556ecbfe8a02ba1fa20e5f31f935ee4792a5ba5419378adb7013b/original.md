```
e = prediction_error(sys::AbstractStateSpace, d::AbstractIdData, args...; kwargs...)
```

Return the prediction errors `d.y - predict(sys, d, ...)
