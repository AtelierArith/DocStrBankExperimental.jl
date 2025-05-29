```
c = TypeUtils.Converter(f, T::Type)
```

builds a lightweight callable object `c` such that `c(x)` yields `f(T, x)` for any `x`. Converter objects are suitable to map conversion to type `T` by function `f` to collections.

This is similar to `Base.Fix1(f,T)` except that `sizeof(Base.Fix1(f,T)) = sizeof(Int)` while `sizeof(TypeUtils.Converter(f,T)) = 0`.
