```
NormGrowthCap(τ = 1.01; ϵ = 1e-8, lb = 1e-7, throw = true, scale = true)
```

Gradient norm growth limiter. `τ` controls the maximum that the gradient norm can grow from one step to the next, such that if `||dx||/||dx_prev|| > τ` & `||dx|| > lb`, then `dx = dx * τ*||dx_prev||/(||dx||+ϵ)` Inspired by [Chen et al.](https://arxiv.org/abs/2410.01623) and used with Apollo in [Zhu et al.](https://arxiv.org/abs/2412.05270), but with Optimisers.jl this will apply per-tensor instead of per-model. This implementation also introduces `lb` as a hard minimum on the gradient norm threshold, and never rescales grads below this, preventing a tensor from getting "trapped" near zero. This can be a fixed min, or scaled by the square root of the number of parameters in the tensor (with `scale = true`).
