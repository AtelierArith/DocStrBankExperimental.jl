```
values_as(vnv::VarNamedVector[, T])
```

Return the values/realizations in `vnv` as type `T`, if implemented.

If no type `T` is provided, return values as stored in `vnv`.

# Examples

```jldoctest
julia> using DynamicPPL: VarNamedVector

julia> vnv = VarNamedVector(@varname(x) => 1, @varname(y) => [2.0]);

julia> values_as(vnv) == [1.0, 2.0]
true

julia> values_as(vnv, Vector{Float32}) == Vector{Float32}([1.0, 2.0])
true

julia> values_as(vnv, OrderedDict) == OrderedDict(@varname(x) => 1.0, @varname(y) => [2.0])
true

julia> values_as(vnv, NamedTuple) == (x = 1.0, y = [2.0])
true
```
