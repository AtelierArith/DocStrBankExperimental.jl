```
CRP(lrp_analyzer, layer, features)
```

Use Concept Relevance Propagation to explain the output of a neural network with respect to specific features in a given layer.

# Arguments

  * `lrp_analyzer::LRP`: LRP analyzer
  * `layer::Int`: Index of layer after which the concept is located
  * `features`: Concept / feature to explain.

See also [`TopNFeatures`](@ref) and [`IndexedFeatures`](@ref).

# References

[1] R. Achtibat et al., From attribution maps to human-understandable explanations     through Concept Relevance Propagation
