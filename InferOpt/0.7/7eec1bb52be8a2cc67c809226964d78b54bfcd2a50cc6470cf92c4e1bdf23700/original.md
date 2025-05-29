```julia
struct Pushforward{O<:InferOpt.AbstractOptimizationLayer, P} <: InferOpt.AbstractLayer
```

Differentiable pushforward of a probabilistic optimization layer with an arbitrary function post-processing function.

`Pushforward` can be used for direct regret minimization (aka learning by experience) when the post-processing returns a cost.

# Fields

  * `optimization_layer::InferOpt.AbstractOptimizationLayer`: probabilistic optimization layer
  * `post_processing::Any`: callable
