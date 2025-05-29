```
resampled_as(src_var::OutputVar, dest_var::OutputVar, dim_names = nothing)
```

Resample `data` in `src_var` to `dims` in `dest_var`.

The resampling performed here is a 1st-order linear resampling.

If the string or iterable `dim_names` is `nothing`, then resampling is done over all dimensions. Otherwise, resampling is done over the dimensions in `dim_names`.

!!! note "Automatic reordering"
    If resampling is done over all dimensions, then reordering the dimensions of the resulting `OutputVar` is automatically done.


The correct dimension to resample on is identified by using `conventional_dim_name`. For example, if `src_var` has a longitude dimension named `lon`, `dest_var` has a longitude dimension named `long`, and `dim_names` is `longitude`, then resampling is done on the longitude dimension because `conventional_dim_name` maps `lon`, `long`, and `longitude` to `longitude`.

!!! compat "`dim_names` keyword argument"
    The keyword argument `dim_names` is introduced in ClimaAnalysis v0.5.14.

