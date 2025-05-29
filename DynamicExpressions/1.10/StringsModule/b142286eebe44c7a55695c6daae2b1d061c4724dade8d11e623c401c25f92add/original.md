```
string_tree(
    tree::AbstractExpressionNode{T},
    operators::Union{AbstractOperatorEnum,Nothing}=nothing;
    f_variable::F1=string_variable,
    f_constant::F2=string_constant,
    variable_names::Union{Array{String,1},Nothing}=nothing,
    # Deprecated
    varMap=nothing,
)::String where {T,F1<:Function,F2<:Function}
```

Convert an equation to a string.

# Arguments

  * `tree`: the tree to convert to a string
  * `operators`: the operators used to define the tree

# Keyword Arguments

  * `f_variable`: (optional) function to convert a variable to a string, with arguments `(feature::UInt8, variable_names)`.
  * `f_constant`: (optional) function to convert a constant to a string, with arguments `(val,)`
  * `variable_names::Union{Array{String, 1}, Nothing}=nothing`: (optional) what variables to print for each feature.
