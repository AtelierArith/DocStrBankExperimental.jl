```
construct(T::Type, val, fmt::Format [, ctx::Context])::T
```

Postprocess a value `val` unpacked according to `fmt` and return an object of type `T`. The type of `val` depends on the format `fmt` that was used for unpacking.

Defaults to `T(val)` but can be overwritten for any combination of `T`, `fmt`, and `ctx`.
