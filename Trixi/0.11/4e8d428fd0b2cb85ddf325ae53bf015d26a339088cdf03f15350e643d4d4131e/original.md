```
convergence_test([mod::Module=Main,] elixir::AbstractString, iterations, RealT = Float64; kwargs...)
```

Run `iterations` Trixi.jl simulations using the setup given in `elixir` and compute the experimental order of convergence (EOC) in the $L^2$ and $L^\infty$ norm. Use `RealT` as the data type to represent the errors. In each iteration, the resolution of the respective mesh will be doubled. Additional keyword arguments `kwargs...` and the optional module `mod` are passed directly to [`trixi_include`](@ref).

This function assumes that the spatial resolution is set via the keywords `initial_refinement_level` (an integer) or `cells_per_dimension` (a tuple of integers, one per spatial dimension).
