```julia
ZygoteVJP <: VJPChoice
```

Uses Zygote.jl to compute vector-Jacobian products. Tends to be the fastest VJP method if the ODE/DAE/SDE/DDE is written with mostly vectorized  functions (like neural networks and other layers from Flux.jl) and the `f` function is given out-of-place. If the `f` function is in-place, then `Zygote.Buffer` arrays are used internally, which can greatly reduce the performance of the VJP method.

## Constructor

```julia
ZygoteVJP(; allow_nothing = false)
```

Keyword arguments:

  * `allow_nothing`: whether `nothing`s should be implicitly converted to zeros. In Zygote, the derivative of a function with respect to `p` which does not use `p` in any possible calculation is given a derivative of `nothing` instead of zero. By default, this `nothing` is caught in order to throw an informative error message about a potentially unintentional misdefined function. However, if this was intentional, setting `allow_nothing=true` will remove the error message.
