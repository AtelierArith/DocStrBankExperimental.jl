```
ForwardDiffGrad(chunk_size::Int)
```

The auto-differentiation backend for the CVI procedure. Uses the `ForwardDiff` library to compute gradients/derivatives. If `chunk_size` is not specified then uses the heuristic from `ForwardDiff`, which is type-unstable.

!!! note
    The `ForwardDiff.jl` must be added to the current Julia environment.

