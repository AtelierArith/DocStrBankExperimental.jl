```
string_tree(tree::AbstractExpressionNode, options::AbstractOptions; kws...)
```

Convert an equation to a string.

# Arguments

  * `tree::AbstractExpressionNode`: The equation to convert to a string.
  * `options::AbstractOptions`: The options holding the definition of operators.
  * `variable_names::Union{Array{String, 1}, Nothing}=nothing`: what variables   to print for each feature.
