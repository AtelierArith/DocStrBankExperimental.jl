```
IdentityRelaxation <: AbstractOptimizationLayer
```

Naive relaxation of a black-box optimizer where constraints are simply forgotten.

Consider (centering and) normalizing `θ` before applying it.

# Fields

  * `maximizer`: underlying argmax function

Reference: [https://arxiv.org/abs/2205.15213](https://arxiv.org/abs/2205.15213)
