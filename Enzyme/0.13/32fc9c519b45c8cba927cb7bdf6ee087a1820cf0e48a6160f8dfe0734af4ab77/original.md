```
autodiff_deferred(::ForwardMode, f, Activity, args::Annotation...)
```

Same as `autodiff(::ForwardMode, f, Activity, args...)` but uses deferred compilation to support usage in GPU code, as well as high-order differentiation.
