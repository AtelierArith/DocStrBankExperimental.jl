```
train_flow([rng::AbstractRNG, ]vo, flow, args...; kwargs...)
```

Train the given normalizing flow `flow` by calling `optimize`.

# Arguments

  * `rng::AbstractRNG`: random number generator
  * `vo`: variational objective
  * `flow`: normalizing flow to be trained, we recommend to define flow as `<:Bijectors.TransformedDistribution`
  * `args...`: additional arguments for `vo`

# Keyword Arguments

  * `max_iters::Int=1000`: maximum number of iterations
  * `optimiser::Optimisers.AbstractRule=Optimisers.ADAM()`: optimiser to compute the steps
  * `ADbackend::ADTypes.AbstractADType=ADTypes.AutoZygote()`:    automatic differentiation backend, currently supports   `ADTypes.AutoZygote()`, `ADTypes.ForwardDiff()`, `ADTypes.ReverseDiff()`,    `ADTypes.AutoMooncake()` and   `ADTypes.AutoEnzyme(;       mode=Enzyme.set_runtime_activity(Enzyme.Reverse),       function_annotation=Enzyme.Const,   )`.   If user wants to use `AutoEnzyme`, please make sure to include the `set_runtime_activity` and `function_annotation` as shown above.
  * `kwargs...`: additional keyword arguments for `optimize` (See [`optimize`](@ref) for details)

# Returns

  * `flow_trained`: trained normalizing flow
  * `opt_stats`: statistics of the optimiser during the training process    (See [`optimize`](@ref) for details)
  * `st`: optimiser state for potential continuation of training
