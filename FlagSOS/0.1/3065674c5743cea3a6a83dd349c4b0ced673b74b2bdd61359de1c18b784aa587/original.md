```
PartiallyColoredFlag{T} <: Flag where {T<:Flag}
```

A Flag `F` where (some of) the `n` vertices are colored. May have isolated vertices. Assumes vertices are ordered by color, with uncolored vertices at the end. Labeling such a Flag canonically cannot swap vertices with different colors, meaning the Flags 2-1-o and 1-2-o are different. If swaps there should be allowed, use a `ColoredFlag{T}` instead.
