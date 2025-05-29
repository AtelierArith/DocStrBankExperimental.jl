Function to determine the coverage dependency, order dependency and MWC for a reaction

# Usage

```
get_dependencies(cov_dep_rxns,order_dep_rxns,mwc_rxns,rxn_id)
```

  * cov*dep*rxns::Dict{Int64=>Dict{Int64=>Float64}}
  * order*dep*rxns::Dict{Int64=>Dict{Int64=>Float64}}
  * mwc_rxns::Array{Int64}
  * rxn_id::Int64

The function returns a tuple of cov,order and mwc
