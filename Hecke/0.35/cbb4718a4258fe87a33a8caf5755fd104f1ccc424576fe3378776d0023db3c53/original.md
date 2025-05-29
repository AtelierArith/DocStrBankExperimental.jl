```
multiplicities(s::MSet{T}) -> ValueIterator{Dict{T, Int}}
```

Return an iterator for the multiplicities of all the elements in `s`.

# Examples

```jldoctest
julia> m = multiset([1,1,2,3,4,4,5])
MSet{Int64} with 7 elements:
  5
  4 : 2
  2
  3
  1 : 2

julia> mult_m = multiplicities(m)
ValueIterator for a Dict{Int64, Int64} with 5 entries. Values:
  1
  2
  1
  1
  2

julia> collect(mult_m)
5-element Vector{Int64}:
 1
 2
 1
 1
 2
```
