```
sctransform([T=Float64], counts::DataMatrix; verbose=true, kwargs...)
```

Compute the SCTransform of the DataMatrix `counts`. The result is stored as a Matrix Expression with the sum of a sparse and a low-rank term. I.e. no large dense matrix is created.

Optionally, `T` can be specified to control the `eltype` of the sparse transformed matrix. `T=Float32` can be used to lower the memory usage, with little impact on the results, since downstream analysis is still done with Float64.

See `SCTransformModel` for description of `kwargs...`.

# Examples

Compute SCTransform (Gene Expression features):

```
julia> sctransform(counts)
```

Compute SCTransform (Antibody Capture features):

```
julia> sctransform(counts; var_filter = :feature_type => isequal("Antibody Capture"))
```

Compute SCTransform (Gene Expression features), using eltype Float32 to lower memory usage:

```
julia> sctransform(Float32, counts)
```

See also: [`SCTransformModel`](@ref), [`SCTransform.scparams`](https://github.com/rasmushenningsson/SCTransform.jl)
