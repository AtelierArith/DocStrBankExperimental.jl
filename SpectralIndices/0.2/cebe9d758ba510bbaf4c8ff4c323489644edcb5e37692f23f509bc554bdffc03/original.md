```
compute_index(index::String, params::Dict=Dict(), online::Bool=false; kwargs...) -> Any
```

Computes one or more Spectral Indices from a predefined list, based on the provided index name, parameters, and optional keyword arguments.

# Parameters

  * `index`: Name of the spectral index or a list of index names to compute.
  * `params`: (Optional) Dictionary of parameters used as inputs for the computation. If not provided, parameters can be passed using keyword arguments.
  * `online`: (Optional) Flag indicating whether to retrieve the most recent list of indices online.
  * `kwargs`: Additional parameters used as inputs for the computation, provided as keyword pairs.

# Returns

  * Computed Spectral Indices, the type of return value depends on the input parameters.

# Examples

```julia-repl
julia> compute_index("NDVI"; N=0.643, R=0.175)

```

```julia-repl
julia> compute_index("NDVI"; N=fill(0.643, (5, 5)), R=fill(0.175, (5, 5)))

```

```julia-repl
julia> compute_index("NDVI"; N=fill(0.643, 5), R=fill(0.175, 5))

```

```julia-repl
julia> compute_index(["NDVI", "SAVI"]; N=fill(0.643, 5), R=fill(0.175, 5), L=fill(0.5, 5))

```

```julia-repl
julia> compute_index(["NDVI", "SAVI"]; N=0.643, R=0.175, L=0.5)

```

```julia-repl
julia> compute_index(
           ["NDVI", "SAVI"]; N=fill(0.643, (5, 5)), R=fill(0.175, (5, 5)), L=fill(0.5, (5, 5))
       )

```
