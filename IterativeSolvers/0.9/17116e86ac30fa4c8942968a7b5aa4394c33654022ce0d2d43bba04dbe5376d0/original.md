Store general and in-depth information about an iterative method.

# Fields

`mvps::Int`: number of matrix vector products.

`mtvps::Int`: number of transposed matrix-vector products

`iters::Int`: iterations taken by the method.

`restart::T`: restart relevant information.

  * `T == Int`: iterations per restart.
  * `T == Nothing`: methods without restarts.

`isconverged::Bool`: convergence of the method.

`data::Dict{Symbol,Any}`: Stores all the information stored during the method execution. It stores tolerances, residuals and other information, e.g. Ritz values in [`svdl`](@ref).

# Constructors

```
ConvergenceHistory()
ConvergenceHistory(restart)
```

Create `ConvergenceHistory` with empty fields.

# Arguments

`restart`: number of iterations per restart.

# Plots

Supports plots using the `Plots.jl` package via a type recipe. Vectors are ploted as series and matrices as scatterplots.

# Implements

`Base`: `getindex`, `setindex!`, `push!`
