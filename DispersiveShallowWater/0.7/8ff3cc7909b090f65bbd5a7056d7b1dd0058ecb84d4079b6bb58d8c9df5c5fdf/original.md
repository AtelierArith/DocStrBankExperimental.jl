```
convergence_test([mod::Module=Main,] example::AbstractString, iterations; io::IO = stdout, kwargs...)
convergence_test([mod::Module=Main,] example::AbstractString, Ns::AbstractVector; io::IO = stdout, kwargs...)
```

Run multiple simulations using the setup given in `example` and compute the experimental order of convergence (EOC) in the $L^2$ and $L^\infty$ norm. If `iterations` is passed as integer, in each iteration, the resolution of the respective mesh will be doubled. If `Ns` is passed as vector, the simulations will be run for each value of `Ns`. Additional keyword arguments `kwargs...` and the optional module `mod` are passed directly to [`trixi_include`](@ref).

Adjusted from [Trixi.jl](https://github.com/trixi-framework/Trixi.jl).
