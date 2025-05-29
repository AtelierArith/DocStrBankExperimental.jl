```
LaSRMutationWeights <: AbstractMutationWeights
```

Defines the composite weights for all the mutation operations in the LaSR module. In addition to the mutation weights     defined in [`MutationWeights`](@ref SymbolicRegression.CoreModule.MutationWeightsModule.MutationWeights), this struct     also includes the weights for the LLM mutation operations. These LLM weights can either be manually set or we will     set them programmatically based on llm*operation*weights. The weights are normalized to sum to 1.0.

# See Also

  * [`AbstractMutationWeights`](@ref SymbolicRegression.CoreModule.MutationWeightsModule.AbstractMutationWeights): Use to define custom mutation weight types.
  * [`MutationWeights`](@ref SymbolicRegression.CoreModule.MutationWeightsModule.MutationWeights): The default mutation weights for the SR module.
