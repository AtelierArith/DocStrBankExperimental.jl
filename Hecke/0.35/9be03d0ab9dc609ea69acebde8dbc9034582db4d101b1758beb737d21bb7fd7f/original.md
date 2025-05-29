```
MSet{T} <: AbstractSet{T}
```

Type for a multi-set, i.e. a set where elements are not unique, they (can) have a multiplicity. `MSet`s can be created from any finite iterator.

# Examples

```jldoctest
julia> MSet([1,1,2,3,4,4,5])
MSet{Int64} with 7 elements:
  5
  4 : 2
  2
  3
  1 : 2
```

`4 : 2` means the element `4` has multiplicity `2`, i.e. was included twice.
