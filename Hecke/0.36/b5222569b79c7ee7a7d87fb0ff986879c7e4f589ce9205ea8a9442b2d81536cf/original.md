```
multiset(iter) -> MSet{eltype(iter)}
multiset(d::Dict{T, Int}) -> MSet{T}
multiset{l::Vector{T}, m::Vector{Int}} -> MSet{T}
```

Given either:

  * a finite iterator `iter`;
  * a dictionary `d` whose values are positive integers;
  * a list `l` and a list of positive integers `m` of same length as `l`;

return the asscciated multi-set `M`.

# Examples

```jldoctest
julia> str = "A nice sentence"
"A nice sentence"

julia> multiset(str)
MSet{Char} with 15 elements:
  'n' : 3
  'A'
  'c' : 2
  'i'
  'e' : 4
  's'
  't'
  ' ' : 2

julia> multiset(Int[x^3%8 for x = 1:50])
MSet{Int64} with 50 elements:
  0 : 25
  5 : 6
  7 : 6
  3 : 6
  1 : 7

julia> d = Dict("a" => 4, "b" => 1, "c" =>9)
Dict{String, Int64} with 3 entries:
  "c" => 9
  "b" => 1
  "a" => 4

julia> multiset(d)
MSet{String} with 14 elements:
  "c" : 9
  "b"
  "a" : 4

julia> multiset(["a", "b", "c"], [4, 1, 9])
MSet{String} with 14 elements:
  "c" : 9
  "b"
  "a" : 4
```
