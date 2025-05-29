```
trixi_include([mapexpr::Function=identity,] [mod::Module=Main,] elixir::AbstractString; kwargs...)
```

`include` the file `elixir` and evaluate its content in the global scope of module `mod`. You can override specific assignments in `elixir` by supplying keyword arguments. Its basic purpose is to make it easier to modify some parameters while running simulations from the REPL. Additionally, this is used in tests to reduce the computational burden for CI while still providing examples with sensible default values for users.

Before replacing assignments in `elixir`, the keyword argument `maxiters` is inserted into calls to `solve` with it's default value used in the SciML ecosystem for ODEs, see the "Miscellaneous" section of the [documentation](https://docs.sciml.ai/DiffEqDocs/stable/basics/common_solver_opts/).

The optional first argument `mapexpr` can be used to transform the included code before it is evaluated: for each parsed expression `expr` in `elixir`, the `include` function actually evaluates `mapexpr(expr)`. If it is omitted, `mapexpr` defaults to `identity`.

# Examples

```@example
julia> using TrixiBase, Trixi

julia> redirect_stdout(devnull) do
         trixi_include(@__MODULE__, joinpath(examples_dir(), "tree_1d_dgsem", "elixir_advection_extended.jl"),
                       tspan=(0.0, 0.1))
         sol.t[end]
       end
[ Info: You just called `trixi_include`. Julia may now compile the code, please be patient.
0.1
```
