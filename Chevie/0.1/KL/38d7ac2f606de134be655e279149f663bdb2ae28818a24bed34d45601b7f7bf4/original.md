`left_cells(W[,i])` left cells of `W` [in `i`-th 2-sided cell] for the 1-parameter Hecke algebra `hecke(W,q)`

The  program uses precomputed  data(see [Geck-Halls 2014](biblio.htm#GH14)) for  exceptional types and for type `:A`,  so is quite fast for these types (it  takes 13 seconds to compute the  101796 left cells for type `E₈`). For other  types, left cells are computed from first principles, thus computing many  Kazhdan-Lusztig polynomials. It takes 30  seconds to compute the left cells of `D₆`, for example.

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> left_cells(W)
4-element Vector{LeftCell{FiniteCoxeterGroup{Perm{Int16},Int64}}}:
 LeftCell<G₂: duflo= character=φ₁‚₀>
 LeftCell<G₂: duflo=12 character=φ₁‚₆>
 LeftCell<G₂: duflo=2 character=φ₂‚₁+φ′₁‚₃+φ₂‚₂>
 LeftCell<G₂: duflo=1 character=φ₂‚₁+φ″₁‚₃+φ₂‚₂>
```

Printing such a record displays the character afforded by the left cell and its  Duflo involution; the Duflo involution `r`  is printed as a subset `I` of   `1:nref(W)`   such   that  `r=longest(reflection_subgroup(W,I))`,  see `describe_involution`.

If  a second argument `i` is given, the program returns only the left cells which  are in the `i`-th two-sided cell,  that is whose character is in the `i`-th family of `W` (see [`Families`](@ref)).

```julia-repl
julia> W=coxgroup(:G,2);
julia> left_cells(W,1)
2-element Vector{LeftCell{FiniteCoxeterGroup{Perm{Int16},Int64}}}:
 LeftCell<G₂: duflo=2 character=φ₂‚₁+φ′₁‚₃+φ₂‚₂>
 LeftCell<G₂: duflo=1 character=φ₂‚₁+φ″₁‚₃+φ₂‚₂>
```
