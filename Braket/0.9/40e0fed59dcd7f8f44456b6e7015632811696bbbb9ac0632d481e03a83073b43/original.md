```
Amplitude(c::Circuit, states) -> Circuit
```

Constructs an `Amplitude` measurement of `states` and adds it as a result to [`Circuit`](@ref) `c`.

`states` may be of type:

  * `Vector{String}`
  * `String`

All elements of `states` must be `'0'` or `'1'`.

# Examples

```jldoctest
julia> c = Circuit();

julia> c = H(c, collect(0:3));

julia> c = Amplitude(c, "0000");
```
