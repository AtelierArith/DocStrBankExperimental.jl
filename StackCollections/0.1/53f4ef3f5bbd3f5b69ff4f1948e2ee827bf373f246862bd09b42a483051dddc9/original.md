```
delete(s::AbstractStackSet, v::Int)
```

Return a copy of `s` that does not contain without `v`.

# Examples

```jldoctest
julia> s = DigitSet([4, 41, 9]);

julia> delete(s, 1)
DigitSet with 3 elements:
  4
  9
  41
```

See also: [`pop`](@ref)
