```
AlgoData(; kwargs...) 
AlgoData(T::DataType; kwargs...)
```

Structure containing all the parameters used in the [`fps_solve`](@ref) call. `T` is the datatype used in the algorithm, by default it is `Float64`. Returns a `AlgoData` structure.

# Arguments

The keyword arguments may include:

  * `σ_0::Real = T(1e3)`: Initialize subproblem's parameter σ;
  * `σ_max::Real = 1 / √eps(T)`: Maximum value for subproblem's parameter σ;
  * `σ_update::Real = T(2)`: Update subproblem's parameter σ;
  * `ρ_0::Real = one(T)`: Initialize subproblem's parameter ρ;
  * `ρ_max::Real = 1 / √eps(T)`: Maximum value for subproblem's parameter ρ;
  * `ρ_update::Real = T(2)`: Update subproblem's parameter ρ;
  * `δ_0::Real = √eps(T)`: Initialize subproblem's parameter δ;
  * `δ_max::Real = 1 / √eps(T)`: Maximum value for subproblem's parameter δ;
  * `δ_update::Real = T(10)`: Update subproblem's parameter δ;
  * `η_1::Real = zero(T)`: Initialize subproblem's parameter η;
  * `η_update::Real = one(T)`: Update subproblem's parameter η;
  * `yM::Real = typemax(T)`: bound on the Lagrange multipliers;
  * `Δ::Real = T(0.95)`: expected decrease in feasibility between two iterations;
  * `subproblem_solver::Function = ipopt`: solver used for the subproblem;
  * `subpb_unbounded_threshold::Real = 1 / √eps(T)`: below the opposite of this value, the subproblem is unbounded;
  * `subsolver_max_iter::Int = 20000`: maximum of iteration for the subproblem solver;
  * `atol_sub::Function = atol -> atol`: absolute tolerance for the subproblem in function of `atol`;
  * `rtol_sub::Function = rtol -> rtol`: relative tolerance for the subproblem in function of `rtol`;
  * `hessian_approx = Val(2)`: either `Val(1)` or `Val(2)`, it selects the hessian approximation;
  * `convex_subproblem::Bool = false`: true if the subproblem is convex. Useful to set the `convex` option in `knitro`;
  * `lagrange_bound::T = 1 / sqrt(eps(T))`: upper-bound on the Lagrange multiplier.

For more details, we refer to the package documentation [fine-tuneFPS.md](https://JuliaSmoothOptimizers.github.io/FletcherPenaltySolver.jl/dev/fine-tuneFPS/). 
