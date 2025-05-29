```
struct FinalJets
```

A struct with the vector of all jets for a certain jet identifier, used for JSON serialisation.

# Fields

  * `jetid::Int64`: The ID of the jet.
  * `jets::Vector{FinalJet}`: A vector of `FinalJet` objects representing the jets.
