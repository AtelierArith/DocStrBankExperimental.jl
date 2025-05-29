```
nearest(T::Type, x) -> y::T
```

yields the value or instance of type `T` that is the nearest to `x`. For `T` integer and `x` real, it can be seen as rounding with clamping.
