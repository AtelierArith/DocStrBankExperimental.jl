```
StringVector(v::CategoricalVector{String})
```

Convert `v::CategoricalVector` efficiently to WeakRefStrings.StringVector

## Example

```julia
using DataFrames
a  = categorical(["a","c", "a"])
a.refs
a.pool.index

# efficiently convert
sa = StringVector(a)

sa.buffer
sa.lengths
sa.offsets
```
