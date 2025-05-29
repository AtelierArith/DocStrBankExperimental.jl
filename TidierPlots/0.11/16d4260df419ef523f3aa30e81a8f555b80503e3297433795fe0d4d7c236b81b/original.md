```
label_bytes(;units=:si, kwargs...)
```

Convert numeric values into human-readable strings representing byte sizes.

# Arguments

  * `units`: Can be `:si` for SI units (powers of 10), `:binary` for binary units (powers of 1024), or a specific unit string (e.g., MB, GiB).
  * `kwargs...`: Additional keyword arguments passed to `label_number`.

# Examples

```julia
labeler = label_bytes(units=:si)
labeler([1024, 2048]) # ["1.02 KB", "2.05 KB"]
```
