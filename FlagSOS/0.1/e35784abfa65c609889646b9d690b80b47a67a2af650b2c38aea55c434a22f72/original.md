```
aut(F::T)::NamedTuple{(:gen, :size),Tuple{Vector{Vector{Int64}},Int64}} where {T<:Flag}
```

The automorphisms of `F`. Returns a named tuple with fields

  * `gen::Vector{Vector{Int}}`: Vector of permutations generating all automorphisms.
  * `size::Int`: The size of the automorphism group of `F`.
