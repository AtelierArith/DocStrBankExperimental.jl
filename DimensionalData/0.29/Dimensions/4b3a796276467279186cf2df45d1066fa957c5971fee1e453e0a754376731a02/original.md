```
Dim{S}(val=:)
```

A generic dimension. For use when custom dims are required when loading data from a file. Can be used as keyword arguments for indexing.

Dimension types take precedence over same named `Dim` types when indexing with symbols, or e.g. creating Tables.jl keys.

```jldoctest; setup = :(using DimensionalData)
julia> dim = Dim{:custom}(['a', 'b', 'c'])
custom ['a', 'b', 'c']
```
