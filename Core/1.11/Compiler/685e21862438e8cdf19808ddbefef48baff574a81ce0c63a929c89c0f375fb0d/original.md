```
widenreturn(𝕃ᵢ::AbstractLattice, @nospecialize(rt), info::BestguessInfo) -> new_bestguess
widenreturn_noslotwrapper(𝕃ᵢ::AbstractLattice, @nospecialize(rt), info::BestguessInfo) -> new_bestguess
```

Appropriately converts inferred type of a return value `rt` to such a type that we know we can store in the cache and is valid and good inter-procedurally, E.g. if `rt isa Conditional` then `rt` should be converted to `InterConditional` or the other cacheable lattice element.

External lattice `𝕃ᵢ::ExternalLattice` may overload:

  * `widenreturn(𝕃ᵢ::ExternalLattice, @nospecialize(rt), info::BestguessInfo)`
  * `widenreturn_noslotwrapper(𝕃ᵢ::ExternalLattice, @nospecialize(rt), info::BestguessInfo)`
