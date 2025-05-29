```
label_pvalue(;precision=2, kwargs...)
```

Format p-values, handling very small or large values with special notation.

# Arguments

  * `precision`: Number of decimal places for thresholding small values.
  * `kwargs`: Additional keyword arguments passed to `label_number`.

# Examples

```julia
labeler = label_pvalue()
labeler([0.0001, 0.05, 0.9999]) # ["<0.01", "0.05", ">0.99"]
```
