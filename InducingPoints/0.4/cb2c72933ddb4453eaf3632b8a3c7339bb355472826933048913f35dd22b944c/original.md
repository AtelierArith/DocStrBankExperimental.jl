```
 inducingpoints([rng::AbstractRNG], alg::Greedy, X::AbstractVector; 
    y::AbstractVector, kernel::Kernel, noise::Real)
 inducingpoints([rng::AbstractRNG], alg::Greedy, X::AbstractMatrix; 
    obsdim=1, y::AbstractVector, kernel::Kernel, noise::Real)
```

Select inducing points according using the Greedy algorithm. Requires as additional keyword arguments the outputs `y`, the `kernel` and the `noise`.
