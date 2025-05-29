```
soundsc(x, S::Real = framerate(x), args...; kwargs...)
```

Call `sound` after scaling `x` to have values in `(-1,1)`.
