```
calc_connected_components(data::Dict{String,<:Any}; edges::Union{Missing, Vector{<:String}}=missing, type::Union{Missing,String}=missing, check_enabled::Bool=true)::Set
```

computes the connected components of the network graph returns a set of sets of bus ids, each set is a connected component

This function differs from the powermodelsdistribution implementation of this functionality in that it accounts for edges being damaged (with the option to harden them) - which functionally makes     these edges act like switches in the context of computing load blocks

In computing connected components, the default is to ignore expansion edges (branch*ne, switch*inline_ne)
