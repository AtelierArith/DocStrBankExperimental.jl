Sorted set of `UnitRange`s. Sorted in ascending order and no one range overlaps with another.

```julia
mutable struct VecUnitRangesSortedSet{K,TU} <: AbstractSet{TU}
    "Index of last used range."
    lastusedrangeindex::Int
    "Storage for ranges starts,"
    rstarts::Vector{K}
    "and stops."
    rstops::Vector{K}
end
```

Ranges stored in `Vector`s: in `rstarts` stored `first`s of ranges, and in `rstops` stored `last`s.

For further details see `UnitRangesSortedSet`.
