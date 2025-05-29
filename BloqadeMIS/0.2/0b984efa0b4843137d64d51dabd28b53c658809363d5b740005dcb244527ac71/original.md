```
mis_postprocessing(graph::AbstractGraph; ntrials::Int = 10)
```

Curried version of [`mis_postprocessing`](@ref).

# Example

to calculate `rydberg_density_sum` loss with postprocessing used in Harvard experiment: [arxiv:2202.09372](https://arxiv.org/abs/2202.09372).

```julia
rydberg_density_sum(mis_postprocessing(graph), reg)
```
