```
pop(s::AbstractStackSet, v::Int)
```

Return a copy of `s` without `v`. If `v` is not in `s`, raise an error.

# Examples

```jldoctest
julia> s = DigitSet([4, 41, 9]);

julia> pop(s, 41)
DigitSet with 2 elements:
  4
  9
```

See also: [`delete`](@ref)
