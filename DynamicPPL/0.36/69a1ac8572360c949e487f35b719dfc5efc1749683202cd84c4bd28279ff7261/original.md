```
Sampler{T}
```

Generic sampler type for inference algorithms of type `T` in DynamicPPL.

`Sampler` should implement the AbstractMCMC interface, and in particular `AbstractMCMC.step`. A default implementation of the initial sampling step is provided that supports resuming sampling from a previous state and setting initial parameter values. It requires to overload [`loadstate`](@ref) and [`initialstep`](@ref) for loading previous states and actually performing the initial sampling step, respectively. Additionally, sometimes one might want to implement [`initialsampler`](@ref) that specifies how the initial parameter values are sampled if they are not provided. By default, values are sampled from the prior.
