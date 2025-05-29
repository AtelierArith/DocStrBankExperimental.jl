```
get_rxn(rxn_string::AbstractString, details::Union{Dict{String,Any},Nothing}=nothing)::Union{Reaction,Nothing}
```

Get a Reaction object from SMARTS. It can only be currently used for depiction purposes.

```julia
rxn = get_rxn("[CH3:1][OH:2]>>[CH2:1]=[OH0:2]")
```
