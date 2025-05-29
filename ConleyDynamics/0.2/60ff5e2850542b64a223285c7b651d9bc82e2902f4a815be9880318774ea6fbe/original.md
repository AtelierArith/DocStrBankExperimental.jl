```
morse_sets(lc::LefschetzComplex, mvf::CellSubsets; poset::Bool=false)
```

Find the nontrivial Morse sets of a multivector field on a Lefschetz complex.

The input argument `lc` contains the Lefschetz complex, and `mvf` describes the multivector field. The function returns the nontrivial Morse sets as a `Vector{Vector{Int}}`. If the optional argument `poset=true` is added, then the function returns both the Morse sets and the adjacency matrix of the Hasse diagram of the underlying poset.
