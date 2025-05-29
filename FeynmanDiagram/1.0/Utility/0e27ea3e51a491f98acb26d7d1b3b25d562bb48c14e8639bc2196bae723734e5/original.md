```
function taylorAD(graphs::Vector{G}, deriv_orders::Vector{Int}, leaf_dep_funcs::Vector{Function};
    dict_graphs::Dict{Vector{Int},Vector{Graph}}=Dict{Vector{Int},Vector{Graph}}()
) where {G<:Graph}

Performs Taylor-mode automatic differentiation (AD) on a vector of graphs, with the differentiation process tailored based on specified maximum orders of differentiation 
and leaf dependency functions. It categorizes the differentiated graphs in a dictionary based on their derivative orders.
```

# Parameters

  * `graphs`: A vector of graphs to be differentiated.
  * `deriv_orders`: A vector of integers specifying the maximum orders of differentiation to apply to the graphs.
  * `leaf_dep_funcs`: A vector of functions determining the dependency of differentiation variables on the properties of leaves in the graphs.
  * `dict_graphs`: Optional. A dictionary for storing the output graphs, keyed by vectors of integers representing the specific differentiation orders. Defaults to an empty dictionary.

# Returns

  * `Dict{Vector{Int},Vector{Graph}}`: A dictionary containing the graphs processed through Taylor-mode AD, categorized by their differentiation orders.

# Example Usage

```julia
# Define a vector of graphs
graphs = [g1, g2]
# Specify the maximum orders of differentiation
deriv_orders = [2, 3, 3]

# Define a vector of differentiation dependency functions for the properties of leaf. 
# The first and second functions specify identify `BareGreenId` and `BareInteractionId` properties as the Green's function and interaction counterterms, respectively.
# The third function specifies the dependence of on the first external momentum of the leaf.
leaf_dep_funcs = [pr -> pr isa FrontEnds.BareGreenId, pr -> pr isa FrontEnds.BareInteractionId, pr -> pr.extK[1] != 0]

# Perform Taylor-mode AD and categorize the results. `result_dict` holds the AD results, organized by differentiation orders `[0:2, 0:3, 0:3]`.
result_dict = taylorAD(graphs, deriv_orders, leaf_dep_funcs)
```
