```
autodiff_deferred(::ReverseMode, f, Activity, args::Annotation...)
```

Same as [`autodiff`](@ref) but uses deferred compilation to support usage in GPU code, as well as high-order differentiation.
