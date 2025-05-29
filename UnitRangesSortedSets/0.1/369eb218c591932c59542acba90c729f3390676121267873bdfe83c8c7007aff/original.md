Sorted set of `UnitRange`s. Sorted in ascending order and no one range overlaps with another.

```julia
mutable struct UnitRangesSortedSet{K,TU} <: AbstractSet{TU}
    "Index of last used range."
    lastusedrangeindex::IntSemiToken
    "Storage for ranges: the key of Dict is the `first(range)`, and the value of Dict is the `last(range)`."
    ranges::SortedDict{K,K,FOrd}
end
```

Ranges stored in `SortedDict` as `first`s in keys and `last`s in values.

`UnitRangesSortedSet` can be created like the standard `Set`:

```julia
    UnitRangesSortedSet(somecontainer)
```

for example

```julia
julia> using UnitRangesSortedSets

julia> UnitRangesSortedSet((1, 2, 4))
UnitRangesSortedSet{Int64} with 2 elements:
  1:2
  4:4

julia> UnitRangesSortedSet(('a':'z', 'α':'ω'))
UnitRangesSortedSet{Char} with 2 elements:
  'a':'z'
  'α':'ω'

julia> Random.seed!(1234);

julia> UnitRangesSortedSet(rand(1:20, 10))
UnitRangesSortedSet{Int64} with 6 elements:
   5:5
   7:8
  10:11
  15:16
  18:18
  20:20
```

or with `push!`:

```julia
julia> urs = UnitRangesSortedSet{Int}()
UnitRangesSortedSet{Int64}()

julia> push!(urs, 1)
UnitRangesSortedSet{Int64} with 1 element:
  1:1

julia> push!(urs, 2)
UnitRangesSortedSet{Int64} with 1 element:
  1:2

julia> push!(urs, 10:12)
UnitRangesSortedSet{Int64} with 2 elements:
   1:2
  10:12
```

Iterating over set of ranges:

```julia
julia> for r in urs @show(r) end
r = 1:2
r = 10:12

julia> for r in urs, i in r @show(i) end
i = 1
i = 2
i = 10
i = 11
i = 12

julia> for i in Iterators.flatten(urs) @show(i) end
i = 1
i = 2
i = 10
i = 11
i = 12

julia> collect(urs)
2-element Vector{UnitRange{Int64}}:
 1:2
 10:12
```

Deleting elements and ranges:

```julia
julia> delete!(urs, 10:11)
UnitRangesSortedSet{Int64} with 2 elements:
   1:2
  12:12

julia> delete!(urs, 1)
UnitRangesSortedSet{Int64} with 2 elements:
   2:2
  12:12
```

Note: for `Char` the `StepRange{Char,UInt8}` with `oneunit(UInt8)` step will be created.
