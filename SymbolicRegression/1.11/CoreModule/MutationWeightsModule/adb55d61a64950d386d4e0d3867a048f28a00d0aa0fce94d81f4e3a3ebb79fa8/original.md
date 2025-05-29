```
AbstractMutationWeights
```

An abstract type that defines the interface for mutation weight structures in the symbolic regression framework. Subtypes of `AbstractMutationWeights` specify how often different mutation operations occur during the mutation process.

You can create custom mutation weight types by subtyping `AbstractMutationWeights` and defining your own mutation operations. Additionally, you can overload the `sample_mutation` function to handle sampling from your custom mutation types.

# Usage

To create a custom mutation weighting scheme with new mutation types, define a new subtype of `AbstractMutationWeights` and implement the necessary fields. Here's an example using `Base.@kwdef` to define the struct with default values:

```julia
using SymbolicRegression: AbstractMutationWeights

# Define custom mutation weights with default values
Base.@kwdef struct MyMutationWeights <: AbstractMutationWeights
    mutate_constant::Float64 = 0.1
    mutate_operator::Float64 = 0.2
    custom_mutation::Float64 = 0.7
end
```

Next, overload the `sample_mutation` function to include your custom mutation types:

```julia
# Define the list of mutation names (symbols)
const MY_MUTATIONS = [
    :mutate_constant,
    :mutate_operator,
    :custom_mutation
]

# Import the `sample_mutation` function to overload it
import SymbolicRegression: sample_mutation
using StatsBase: StatsBase

# Overload the `sample_mutation` function
function sample_mutation(w::MyMutationWeights)
    weights = [
        w.mutate_constant,
        w.mutate_operator,
        w.custom_mutation
    ]
    weights = weights ./ sum(weights)  # Normalize weights to sum to 1.0
    return StatsBase.sample(MY_MUTATIONS, StatsBase.Weights(weights))
end

# Pass it when defining `Options`:
using SymbolicRegression: Options
options = Options(mutation_weights=MyMutationWeights())
```

This allows you to customize the mutation sampling process to include your custom mutations according to their specified weights.

To integrate your custom mutations into the mutation process, ensure that the mutation functions corresponding to your custom mutation types are defined and properly registered with the symbolic regression framework. You may need to define methods for `mutate!` that handle your custom mutation types.

# See Also

  * [`MutationWeights`](@ref): A concrete implementation of `AbstractMutationWeights` that defines default mutation weightings.
  * [`sample_mutation`](@ref): Function to sample a mutation based on current mutation weights.
  * [`mutate!`](@ref SymbolicRegression.MutateModule.mutate!): Function to apply a mutation to an expression tree.
  * [`AbstractOptions`](@ref SymbolicRegression.OptionsStruct.AbstractOptions): See how to extend abstract types for customizing options.
