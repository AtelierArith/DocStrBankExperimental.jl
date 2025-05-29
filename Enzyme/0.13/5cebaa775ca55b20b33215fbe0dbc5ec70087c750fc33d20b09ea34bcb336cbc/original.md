```
autodiff(mode::Mode, f, ::Type{A}, args::Annotation...)
```

Like [`autodiff`](@ref) but will try to extend f to an annotation, if needed.
