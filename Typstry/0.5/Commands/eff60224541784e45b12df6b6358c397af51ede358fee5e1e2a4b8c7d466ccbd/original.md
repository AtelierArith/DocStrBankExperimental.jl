```
@typst_cmd("s")
typst`s`
```

Construct a [`TypstCommand`](@ref) where each parameter is separated by a space.

This does not support interpolation; use the constructor instead.

# Examples

```jldoctest
julia> typst`help`
typst`help`

julia> typst`compile input.typ output.typ`
typst`compile input.typ output.typ`
```
