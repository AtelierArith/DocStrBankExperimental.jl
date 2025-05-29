```
Lineage{T<:AbstractTaxon} <: AbstractVector{T}
```

A type that stores lineage information in `Vector`-like format. `T` represents element types, `Taxon` or `UnclassifiedTaxon`.

  * `getindex` is overloaded to get `Taxon` values. `Symbol`s such as `:superkingdom`, `:family`, `:genus`, `:species` in `CanonicalRanks` can be used. Also, `Between`, `From`, `Until`, `Cols` and `All` selectors can be used in more complex rank selection scenarios.
  * Once reformatted, it cannot be reformatted again. The status can be checked using `isreformatted(lineage)`.
