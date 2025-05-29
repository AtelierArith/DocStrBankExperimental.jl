```
RandomSampler{T<:AbstractRNG} <: Sampler
```

Sample a value for each parameter uniformly at random from the candidate vectors. Log-uniform sampling available by providing a log-spaced candidate vector.

Optionally, pass an `AbstractRNG` to initialize.
