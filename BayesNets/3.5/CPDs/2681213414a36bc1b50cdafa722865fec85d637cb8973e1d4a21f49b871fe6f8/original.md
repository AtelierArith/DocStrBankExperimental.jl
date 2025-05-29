```
strip_arg(arg::Symbol)
```

Strip anything extra (type annotations, default values, etc) from an argument. For now this cannot handle keyword arguments (it will throw an error).
