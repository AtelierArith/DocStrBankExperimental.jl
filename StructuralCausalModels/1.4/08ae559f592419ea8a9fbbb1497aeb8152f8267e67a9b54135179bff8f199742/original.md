# `adjustment_sets`

```julia
adjustment_sets(dag, f, l; debug)

```

Computes the covariance adjustment vertex set. 

### Required arguments

```julia
* `dag::DAG`                           : DAG
* `f::Symbol`                          : Start variable
* `l::Symbol`                          : End variable
```

### Optional arguments

```julia
* `debug::Bool`                        : Show debug trace
```

### Returns

```julia
* `adjustmentsets=Vector{Symbol}[]`    : Array of adjustment sets
```

# Extended help

### Acknowledgements

Original author                        : Rob J Goedman

### Licence

Licenced under: MIT.

Part of the api, exported.
