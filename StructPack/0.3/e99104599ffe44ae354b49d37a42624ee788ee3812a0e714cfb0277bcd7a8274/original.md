```
destruct(val::T, fmt::Format [, ctx::Context])
```

Preprocess a value `val` to prepare packing it in the format `fmt`.

Defaults to `val` but can be overwritten for any combination of `T`, `fmt`, and `ctx`.

Each format has specific requirements regarding the output of this method.
