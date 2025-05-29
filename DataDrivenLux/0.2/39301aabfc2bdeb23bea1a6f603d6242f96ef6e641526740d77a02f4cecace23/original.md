```julia
struct FunctionNode{__T_node} <: LuxCore.AbstractLuxWrapperLayer{:node}
```

A layer representing a decision node with a single function  and a latent array of weights representing a probability distribution over the inputs.

# Fields

  * `node`
