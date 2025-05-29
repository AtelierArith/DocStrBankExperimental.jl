```
OptimizeParameters(kind=MinRecall(0.9);
    initialpopulation=16,
    maxiters=12,
    bsize=4,
    ksearch=10,
    queries=nothing,
    numqueries=32,
    verbose=false,
    params=SearchParams(; maxpopulation=initialpopulation, bsize, mutbsize=4bsize, crossbsize=2bsize, maxiters, verbose),
    space::BeamSearchSpace=BeamSearchSpace()
)
```

Creates a hyperoptimization callback using the given parameters

# Arguments

  * `kind`: The kind of error function, e.g. `MinRecall(0.9)`.
  * `hints`: How search hints should be computed.
  * `initialpopulation`: Optimization argument that determines the initial number of configurations.
  * `maxiters`: Optimization argument that determines the number of iterations.
  * `bsize`: Optimization argument that determines how many top configurations are allowed to mutate and cross.
  * `params`: The `SearchParams` arguments (if separated optimization arguments are not enough)
  * `ksearch`: The number of neighbors to be retrived by the optimization process.
  * `queries`: The queryset to be used during the optimization process.
  * `numqueries`: The number of queries to be performed during the optimization process.
  * `space`: The cofiguration search space

# See more

  * See [`BeamSearchSpace`](@ref)
  * [`SearchParams` arguments of `SearchModels.jl`](https://github.com/sadit/SearchModels.jl)

for more details
