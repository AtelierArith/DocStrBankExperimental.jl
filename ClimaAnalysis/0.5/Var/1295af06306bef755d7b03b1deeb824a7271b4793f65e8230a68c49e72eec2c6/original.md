```
resampled_as(src_var::OutputVar, kwargs...)
```

Resample `data` in `src_var` to dimensions as defined by the keyword arguments.

The resampling performed here is a 1st-order linear resampling.

For example, to resample on the longitude dimension of `[0.0, 1.0, 2.0]`, one can do `resampled_as(src_var, lon = [0.0, 1.0, 2.0])`.

If the dimensions in `dims` and `src_var.dims` match (ignoring order), the resulting `OutputVar` will have its dimensions reordered to match the order in `dims`. Otherwise, the dimensions of the resulting `OutputVar` will remain unchanged. If the dimensions of `dims` is a strict subset of the dimensions in `src_var`, then partial resampling is done instead.

Note that there is no checking for units of the dimensions.
