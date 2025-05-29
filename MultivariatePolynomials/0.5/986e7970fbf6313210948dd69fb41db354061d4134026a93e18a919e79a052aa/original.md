```
struct LazyMap{T, VT}
    f::Function
    data::VT
end
```

Iterator over the elements of `data` mapped by `f`. This is similar to `Base.Generator(f, data)` except that the `eltype` of a `LazyMap` is given at construction while the `eltype` of `Base.Generator(f, data)` is `Any`.
