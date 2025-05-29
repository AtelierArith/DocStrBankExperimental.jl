```
loadrxnetwork(mn::MatrixNetwork; name = gensym(:ReactionSystem))
```

Converts a `MatrixNetwork` into a `ParsedReactionNetwork` by constructing a `ReactionSystem`.

# Arguments

  * `mn::MatrixNetwork`: A `MatrixNetwork` object containing the stoichiometric matrices, rate expressions, species, and parameters.
  * `name::Symbol`: (Optional) Name for the resulting `ReactionSystem`. Defaults to a generated symbol.

# Returns

A `ParsedReactionNetwork` 

# Notes

  * The `MatrixNetwork` must have substrate (`substoich`) and product (`prodstoich`) stoichiometric matrices of the same size.
  * The stoichiometric matrices are assumed to be `numspecies x numrxs`, where each entry `(i, j)` represents the stoichiometric coefficient of species `i` in reaction `j`.
  * If the `species` field in `MatrixNetwork` is empty, species symbols are automatically generated.
  * The `t` field specifies the independent variable (e.g., time). If not provided, a default time variable is used.

# Example

```julia
using Catalyst

# Define a MatrixNetwork
rateexprs = [1.0, 2.0]
substoich = [1 0; 0 1]
prodstoich = [0 1; 1 0]
species = [@species A(t), B(t)]
params = [@parameters k1, k2]
mn = MatrixNetwork(rateexprs, substoich, prodstoich; species = species, params = params)

# Convert to a ParsedReactionNetwork
parsed_network = loadrxnetwork(mn, name = :MyReactionSystem)
```
