```
group_counts(x)
```

Count the number of times that each element of `x` appears.

See also [`group_indices`](@ref)

# Examples

```jldoctest
julia> group_counts(['a', 'b', 'b'])
Dict{Char, Int64} with 2 entries:
  'a' => 1
  'b' => 2
```
