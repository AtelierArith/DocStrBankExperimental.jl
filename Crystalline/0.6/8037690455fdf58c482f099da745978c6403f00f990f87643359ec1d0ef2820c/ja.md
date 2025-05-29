```julia
struct CharacterTable{D} <: Crystalline.AbstractCharacterTable
```

  * `ops::Array{Crystalline.SymOperation{D}, 1} where D`
  * `irlabs::Vector{String}`
  * `table::Matrix{ComplexF64}`
  * `tag::String`
