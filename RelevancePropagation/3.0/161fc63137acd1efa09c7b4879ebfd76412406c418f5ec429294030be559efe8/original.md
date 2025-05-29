```
LRP(model, rules)
LRP(model, composite)
```

Analyze model by applying Layer-Wise Relevance Propagation. The analyzer can either be created by passing an array of LRP-rules or by passing a composite, see [`Composite`](@ref) for an example.

# Keyword arguments

  * `normalize_output_relevance`: Selects whether output relevance should be set to 1 before applying LRP backward pass.   Defaults to `true` to match literature. If `false`, values of output activations are used.
  * `skip_checks::Bool`: Skip checks whether model is compatible with LRP and contains output softmax. Defaults to `false`.
  * `verbose::Bool`: Select whether the model checks should print a summary on failure. Defaults to `true`.

# References

[1] G. Montavon et al., Layer-Wise Relevance Propagation: An Overview [2] W. Samek et al., Explaining Deep Neural Networks and Beyond: A Review of Methods and Applications
