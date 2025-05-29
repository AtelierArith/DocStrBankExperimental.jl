```
Dictionary(indices, undef::UndefInitializer)
```

Construct a `Dictionary` from an iterable of `indices`, where the values are undefined/uninitialized.

# Example

```julia
julia> Dictionary{Int, Float64}([1,2,3], undef)
3-element Dictionary{Int64,Float64}
 1 │ 6.9220016379355e-310
 2 │ 6.9220016379426e-310
 3 │ 6.92200163794736e-310
```
