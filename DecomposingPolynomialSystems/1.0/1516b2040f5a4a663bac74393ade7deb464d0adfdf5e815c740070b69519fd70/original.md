```
sample!(F::SampledSystem; path_ids=Vector(1:nsolutions(F)), n_instances=1) -> SampledSystem
```

Uses [`solve`](https://www.juliahomotopycontinuation.org/HomotopyContinuation.jl/stable/solve/) method to track the solutions of a poynomial system `F` with ids defined by `path_ids` to `n_instances` random parameters.
