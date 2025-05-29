```
convertdict(T::Type, d::AbstractDict)
```

Convert the given dictionary to a object of `T`. `T` must be decorated with `@with_kw` or `@with_kw_noshow` of Parameters.jl.
