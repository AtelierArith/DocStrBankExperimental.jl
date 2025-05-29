```
StdString(str, n::Integer)
```

Create a `StdString` from the first `n` code units of `str` (including null-characters).

## Examples

```julia
julia> StdString("visible\0hidden", 10)
"visible\0hi"
```
