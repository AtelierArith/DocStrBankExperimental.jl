```
result = running_quantile(v, p, w, nan_mode=SkipNaNs())
```

Computes the running `p`-th quantile of the vector `v` with window `w`, where `w` is an odd window length, or a range of offsets. Specifically, 

  * if `w` is a `AbstractUnitRange`, `result[i]` is the `p`-th quantile of `v[(i .+ w) ∩ eachindex(v)]`, where `NaN`s are handled according to `nan_mode`:

      * `nan_mode==SkipNaN()`: `NaN` values are ignored; quantile is computed over non-`NaN`s
      * `nan_mode==PropagateNaNs()`: the result is `NaN` whenever the input window contains `NaN`
      * `nan_mode==ErrOnNaN()`: an error is raise if at least one input window contains `NaN`
  * if `w` is an odd integer, a centered window of length `w` is used, namely `-w÷2:w÷2`

```

```
