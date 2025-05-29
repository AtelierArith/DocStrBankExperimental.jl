```
ReactionNetwork
```

Functions to analyze a PALEOboxes.Model or PALEOmodel output that contains a reaction network

Compiles reaction stoichiometry and rate information from attributes attached to reaction rate variables:

  * rate_processname::String: a process name (eg "photolysis", "reaction", ...)
  * rate_species::Vector{String} names of reactant and product species
  * rate_stoichiometry::Vector{Float64} stoichiometry of reactant and product species
