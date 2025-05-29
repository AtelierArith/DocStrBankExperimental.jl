```
nodf(N::T; dims::Union{Nothing,Integer}=nothing) where {T <: Union{BipartiteNetwork,BipartiteQuantitativeNetwork}}
```

Returns `nodf` for a margin of the network. The `i` argument can be 1 for top-level, 2 for bottom level, and the function will throw an `ArgumentError` if an invalid value is used. For quantitative networks, *WNODF* is used.

###### References

[AlmeidaNeto2008consistent](@citet*)

[AlmeidaNeto2011straightforward](@citet*)
