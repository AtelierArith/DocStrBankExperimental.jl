```
label_log(;base=10, kwargs...)
```

Convert numeric values into logarithmic strings with a specified base.

# Arguments

  * `base`: The logarithmic base.
  * `kwargs`: Additional keyword arguments passed to `label_number`.

# Examples

```julia
labeler = label_log(base=10)
labeler([10, 100]) # ["10^1", "10^2"]
```
