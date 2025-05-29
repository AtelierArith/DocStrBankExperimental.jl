```
compute(si::SpectralIndex, params::Dict=Dict(); kwargs...) -> Any
```

Computes a Spectral Index based on the provided `SpectralIndex` instance, parameters, and optional keyword arguments.

# Parameters

  * `si`: An instance of `SpectralIndex` which includes the name and details of the spectral index to be computed.
  * `params`: (Optional) Dictionary of parameters used as inputs for the computation. If not provided, parameters can be passed using keyword arguments.
  * `kwargs`: Additional parameters used as inputs for the computation, provided as keyword pairs. These are used if `params` is empty.

# Returns

  * The computed Spectral Index, the type of return value depends on the input parameters and the specific spectral index being computed.

# Examples

```julia-repl
julia> compute(NDVI; N=0.643, R=0.175)

```

```julia-repl
julia> compute(NDVI; N=fill(0.643, (5, 5)), R=fill(0.175, (5, 5)))

```
