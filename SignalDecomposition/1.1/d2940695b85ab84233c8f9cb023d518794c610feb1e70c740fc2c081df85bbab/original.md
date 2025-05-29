```
decompose([t, ] s, method::Decomposition) → x, r
```

Decompose an 1D input signal or timeseries `s(t)` into components, `x, r`, using the given `method`. `t` defaults to `1:length(s)`.

What are `x` and `r` really depends on your point of view and your application. They can be structure `x` and noise `r` (i.e. noise reduction). They can be seasonal/periodic `x` and residual component `r`. They can even be multiplier `x` and input `r`.
