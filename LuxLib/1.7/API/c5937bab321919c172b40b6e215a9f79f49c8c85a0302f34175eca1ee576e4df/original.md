```
fast_activation(σ::F, x::AbstractArray) where {F}
```

Compute `σ.(x)` with the best possible implementation available. On CPUs we unroll the loop and use LoopVectorization.jl to vectorize the computation. On GPUs we use simply use broadcasting.

!!! note
    This function doesn't replace `σ` with `NNlib.fast_act(σ, ...)`, that needs to be done by the user if needed.


## Arguments

  * `σ`: Activation function
  * `x`: Input array

## Returns

  * Output Array with the same size as `x`
