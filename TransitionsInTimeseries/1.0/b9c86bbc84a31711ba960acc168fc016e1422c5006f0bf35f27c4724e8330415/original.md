```
windowmap(f::Function, x::AbstractVector; kwargs...) → mapped_f
```

A shortcut for first generating a `wv = WindowViewer(x; kwargs...)` and then applying `mapped_f = map(f, wv)`. If `x` is accompanied by a time vector `t`, you probably also want to call this function with `t` instead of `x` and with one of `mean, midpoint, midvalue` as `f` to obtain a time vector for the `mapped_f` output.
