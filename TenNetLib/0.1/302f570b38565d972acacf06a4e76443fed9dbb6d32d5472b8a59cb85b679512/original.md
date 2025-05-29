```
function bosonize(oppair::Vector{Pair{String, Int}},
                  sites::Vector{Index{T}}) where T
```

Given a string of operator names with positions in the form of `Vector{Pair{String, Int}}` "bosonizes" the operator string by putting the Jordan-Wigner string "F" at appropriate places.

#### Arguments

  * `oppair::Vector{Pair{String, Int}}`: Input string of operator names with positions.
  * `sites::Vector{Index}`: The entire site `Index`s as per ITensors' convention.

#### Return values

  * `::Int`: Even (+1) or odd (-1) permutation.
  * `::Vector{Pair{String, Int}}`:  modified string of operator names and positions.
