```
trixi_include_changeprecision(T, [mod::Module=Main,] elixir::AbstractString; kwargs...)
```

`include` the elixir `elixir` and evaluate its content in the global scope of module `mod`. You can override specific assignments in `elixir` by supplying keyword arguments, similar to [`trixi_include`](@ref).

The only difference to [`trixi_include`](@ref) is that the precision of floating-point numbers in the included elixir is changed to `T`. More precisely, the package [ChangePrecision.jl](https://github.com/JuliaMath/ChangePrecision.jl) is used to convert all `Float64` literals, operations like `/` that produce `Float64` results, and functions like `ones` that return `Float64` arrays by default, to the desired type `T`. See the documentation of ChangePrecision.jl for more details.

The purpose of this function is to conveniently run a full simulation with `Float32`, which is orders of magnitude faster on most GPUs than `Float64`, by just including the elixir with `trixi_include_changeprecision(Float32, elixir)`. Many constructors in the Trixi.jl framework are written in a way that changing all floating-point arguments to `Float32` will change the element type to `Float32` as well. In TrixiParticles.jl, including an elixir with this macro should be sufficient to run the full simulation with single precision.
