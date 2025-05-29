```
getaccumulator(writer::Writer)
```

Returns the accumulator of the Writer value.

## Examples

```jldoctest
julia> using TypeClasses

julia> getaccumulator(Writer("example-accumulator"))
"example-accumulator"
```
