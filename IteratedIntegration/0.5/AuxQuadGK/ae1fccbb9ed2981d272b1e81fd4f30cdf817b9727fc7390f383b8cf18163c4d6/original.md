```
auxquadgk!(f::BatchIntegrand, result, a,b,c...; kws...)
```

Like [`auxquadgk!`](@ref), but batches evaluation points for an in-place integrand to evaluate simultaneously. In particular, there are two differences from using `quadgk` with a `BatchIntegrand`:

1. `f.y` must be an array of dimension `ndims(result)+1` whose first `axes` match those of `result`. The last dimension of `y` should be reserved for different Kronrod points, and the function `f.f!` should be of the form `f!(y,x) = foreach((v,z) -> v .= f(z), eachslice(y, dims=ndims(y)), x)` or

    function f!(y, x)      idx = CartesianIndices(axes(y)[begin:end-1])      for (j,i) in zip(axes(y)[end], eachindex(x))          y[idx,j] .= f(x[i])      end  end
2. `f.y` must be `resize!`-able in the last dimension. Consider using [ElasticArrays.jl](https://github.com/JuliaArrays/ElasticArrays.jl) for this. Otherwise specialize `QuadGK.resizelastdim!(A::T, n)` for your array type `T`.
