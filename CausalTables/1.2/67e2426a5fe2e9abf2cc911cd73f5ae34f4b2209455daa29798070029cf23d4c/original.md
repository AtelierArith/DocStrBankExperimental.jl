```
struct StructuralCausalModel
```

A struct representing a structural causal model (SCM). This includes a DataGeneratingProcess 

# Arguments

  * `dgp::DataGeneratingProcess`: The data generating process from which random data will be drawn.
  * `treatment::Vector{Symbol}`: The variables representing the treatment.
  * `response::Vector{Symbol}`: The variables representing the response.
  * `causes::Union{NamedTuple, Nothing}`: A NamedTuple of Vectors labeling the causes of relevant variables in the data-generating process. If `nothing`, will assume that all variables not contained in `treatment` or `response` are common causes of both.
  * `arraynames`: Names of auxiliary variables used in the DataGeneratingProcess that are not included as "tabular" variables. Most commonly used to denote names of adjacency matrices used to compute summary functions of previous steps.
