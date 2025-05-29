```
soundsc(x, S::Real = framerate(x), args...; kwargs...)
```

`x`をスケーリングして値を`(-1,1)`にした後に`sound`を呼び出します。
