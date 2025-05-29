```
final_jets(jets::Vector{PseudoJet}, ptmin::AbstractFloat=0.0)
```

This function takes a vector of `PseudoJet` objects and a minimum transverse momentum `ptmin` as input. It returns a vector of `FinalJet` objects that satisfy the transverse momentum condition.

# Arguments

  * `jets::Vector{PseudoJet}`: A vector of `PseudoJet` objects representing the input jets.
  * `ptmin::AbstractFloat=0.0`: The minimum transverse momentum required for a jet to be included in the final jets vector.

# Returns

A vector of `FinalJet` objects that satisfy the transverse momentum condition.
