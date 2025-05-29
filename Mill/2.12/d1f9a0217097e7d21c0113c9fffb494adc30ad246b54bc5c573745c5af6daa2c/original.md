```
ProductModel(ms, m=identity)
ProductModel(m=identity; ms...)
```

Construct a [`ProductModel`](@ref) from the arguments. `ms` should an iterable (`Tuple`, `NamedTuple` or `Vector`) of one or more [`AbstractMillModel`](@ref)s.

It is also possible to pass any function as elements of `ms`. In that case, it is wrapped into an [`ArrayNode`](@ref).

# Examples

```jldoctest
julia> ProductModel(a=ArrayModel(Dense(2, 2)), b=identity)
ProductModel ↦ identity
  ├── a: ArrayModel(Dense(2 => 2))  2 arrays, 6 params, 112 bytes
  ╰── b: ArrayModel(identity)

julia> ProductModel(Dense(4, 2); a=ArrayModel(Dense(2, 2)), b=Dense(2, 2))
ProductModel ↦ Dense(4 => 2)  2 arrays, 10 params, 128 bytes
  ├── a: ArrayModel(Dense(2 => 2))  2 arrays, 6 params, 112 bytes
  ╰── b: ArrayModel(Dense(2 => 2))  2 arrays, 6 params, 112 bytes

julia> ProductModel((identity, BagModel(ArrayModel(Dense(2, 2)), SegmentedMean(2), identity)))
ProductModel ↦ identity
  ├── ArrayModel(identity)
  ╰── BagModel ↦ SegmentedMean(2) ↦ identity  1 arrays, 2 params (all zero), 48 bytes
        ╰── ArrayModel(Dense(2 => 2))  2 arrays, 6 params, 112 bytes

julia> ProductModel(identity)
ProductModel ↦ identity
  ╰── ArrayModel(identity)
```

See also: [`AbstractMillModel`](@ref), [`AbstractProductNode`](@ref), [`ProductNode`](@ref).
