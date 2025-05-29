```
solve!(solver::AbstractLinearSolver, b; x0 = 0, callbacks = (_, _) -> nothing)
```

Solves an inverse problem for the data vector `b` using `solver`.

# Required Arguments

  * `solver::AbstractLinearSolver`    - linear solver (e.g., `ADMM` or `FISTA`), containing forward/normal operator and regularizer
  * `b::AbstractVector`               - data vector if `A` was supplied to the solver, back-projection of the data otherwise

# Optional Keyword Arguments

  * `x0::AbstractVector`              - initial guess for the solution; default is zero
  * `callbacks`              - (optionally a vector of) function or callable struct that takes the two arguments `callback(solver, iteration)` and, e.g., stores, prints, or plots the intermediate solutions or convergence parameters. Be sure not to modify `solver` or `iteration` in the callback function as this would japaridze convergence. The default does nothing.

# Examples

The optimization problem

$$
	argmin_x ||Ax - b||_2^2 + λ ||x||_1
$$

can be solved with the following lines of code:

```jldoctest solveExample
julia> using RegularizedLeastSquares

julia> A = [0.831658  0.96717
            0.383056  0.39043
            0.820692  0.08118];

julia> x = [0.5932234523399985; 0.2697534345340015];

julia> b = A * x;

julia> S = ADMM(A, reg = L1Regularization(0.0001));

julia> x_approx = solve!(S, b)
2-element Vector{Float64}:
 0.5932171509222105
 0.26971370566079866
```

Here, we use [`L1Regularization`](@ref). All regularization options can be found in [API for Regularizers](@ref).

The following example solves the same problem, but stores the solution `x` of each interation in `tr`:

```jldoctest solveExample
julia> tr = Dict[]
Dict[]

julia> store_trace!(tr, solver, iteration) = push!(tr, Dict("iteration" => iteration, "x" => solver.x, "beta" => solver.β))
store_trace! (generic function with 1 method)

julia> x_approx = solve!(S, b; callbacks=(solver, iteration) -> store_trace!(tr, solver, iteration))
2-element Vector{Float64}:
 0.5932234523399984
 0.26975343453400163

julia> tr[3]
Dict{String, Any} with 3 entries:
  "iteration" => 2
  "x"         => [0.593223, 0.269753]
  "beta"      => [1.23152, 0.927611]
```

The last example show demonstrates how to plot the solution at every 10th iteration and store the solvers convergence metrics:

```julia
julia> using Plots

julia> conv = StoreConvergenceCallback()

julia> function plot_trace(solver, iteration)
         if iteration % 10 == 0
           display(scatter(solver.x))
         end
       end
plot_trace (generic function with 1 method)

julia> x_approx = solve!(S, b; callbacks = [conv, plot_trace]);
```

The keyword `callbacks` allows you to pass a (vector of) callable objects that takes the arguments `solver` and `iteration` and prints, stores, or plots intermediate result.

See also [`StoreSolutionCallback`](@ref), [`StoreConvergenceCallback`](@ref), [`CompareSolutionCallback`](@ref) for a number of provided callback options.
