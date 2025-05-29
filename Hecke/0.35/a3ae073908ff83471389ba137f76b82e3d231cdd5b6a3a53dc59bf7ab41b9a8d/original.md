```
(+)(s::MSet, itrs...) -> MSet
```

Return the multi-sets associated to the disjoint union of `s` and the collections of objects in `itrs`.

# Examples

```jldoctest
julia> m = multiset("A nice sentence")
MSet{Char} with 15 elements:
  'n' : 3
  'A'
  'c' : 2
  'i'
  'e' : 4
  's'
  't'
  ' ' : 2

julia> n = multiset("A very nice sentence")
MSet{Char} with 20 elements:
  'n' : 3
  'e' : 5
  'A'
  'y'
  'i'
  'r'
  's'
  't'
  ' ' : 3
  'c' : 2
  'v'

julia> m + n
MSet{Char} with 35 elements:
  'n' : 6
  'e' : 9
  'A' : 2
  's' : 2
  'i' : 2
  't' : 2
  'y'
  'r'
  ' ' : 5
  'c' : 4
  'v'
```
