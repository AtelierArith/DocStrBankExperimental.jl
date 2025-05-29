```
SolveTwoStageRO_ECCG(args...; kwargs...)
```

Solve the following two-stage robust optimization problems using Extended Column-and-Constraint Generation (ECCG) method (`Ref.1`):

```formulation
Min_x a' * x + Max_{u ∈ U} Min_{y ∈ Y(x, u)} b' * y

Subject to:

    E * x ≥ e, x ∈ Sx

    Y(x, u) = {y ∈ Sy: A * x + B * y + C * u ≥ c}

    U is the uncertainty set
```

where `Sx` is allowed to be a nonnegative real-valued space or a nonnegative mixed integer space, and `Sy` is allowed to be a nonnegative real-valued space.

P.S. We hope the Feasibility assumption holds, i.e., there **exists** `x ∈ {x ∈ Sx: E * x ≥ e}` such that for any `u ∈ U` the set `Y(x, u) ≠ ∅`, while the Relatively Complete Recourse assumption (i.e., for **any** `x ∈ {x ∈ Sx: E * x ≥ e}` and any `u ∈ U` the set `Y(x, u) ≠ ∅`) doesn't neccessarily hold. (`Ref.1`)

# Arguments

  * `a::AbstractVector{<:Real}`: It should be a vector. A degenerate scalar `a` should be converted into a vector form first, e.g., `a = [2]`.
  * `b::AbstractVector{<:Real}`: It should be a vector. A degenerate scalar `b` should be converted into a vector form first, e.g., `b = [1]`.
  * `E::AbstractMatrix{<:Real}`: It should be a matrix. A degenerate vector or scalar `E` should be converted into a matrix form first, e.g., `E = [1 2]`, `E = [1; 2;;]` or `E = [0;;]`.
  * `e::AbstractVector{<:Real}`: It should be a vector. A degenerate scalar `e` should be converted into a vector form first, e.g., `e = [0]`.
  * `B::AbstractMatrix{<:Real}`: It should be a matrix. A degenerate vector or scalar `B` should be converted into a matrix form first, e.g., `B = [1 2]`, `B = [1; 2;;]` or `B = [1;;]`.
  * `c::AbstractVector{<:Real}`: It should be a vector. A degenerate scalar `c` should be converted into a vector form first, e.g., `c = [0]`.
  * `A::AbstractMatrix{<:Real}`: It should be a matrix. A degenerate vector or scalar `A` should be converted into a matrix form first, e.g., `A = [1 2]`, `A = [1; 2;;]` or `A = [-1;;]`.
  * `C::AbstractMatrix{<:Real}`: It should be a matrix. A degenerate vector or scalar `C` should be converted into a matrix form first, e.g., `C = [1 2]`, `C = [1; 2;;]` or `C = [-1;;]`.
  * `Sx::Vector{<:BasicDomain}`: It is allowed to be a nonnegative real-valued space or a nonnegative mixed integer space. It should be constructed as a vector consisting of (a mixture of) instances of the following three basic data types: `Rplus`, `ZeroOne` and `Zplus`. E.g., `Sy = [ZeroOne()]` denotes an one-dimensional binary space `{0, 1}` and `Sy = [Rplus(2), Zplus(3)]` denotes a five-dimensianal nonnegative mixed integer space `ℝ₊² × ℤ₊³`. Note that the latter is equivalent to `Sy = [fill(Rplus(), 2), fill(Zplus(), 3)]`.
  * `Sy::Vector{<:BasicDomain}`: It is allowed to be a nonnegative real-valued space. The construction method is similar to `Sx`.
  * `U::Union{Model, Polyhedron}`: The uncertainty set is allowed to be constructed as a `Model` using package `JuMP.jl` or a `Polyhedron` using package `Polyhedra.jl`. This package has integrated some neccessary functions from `JuMP.jl`, `Polyhedra.jl` and some other related packages, which allows the user to model the uncertainty set conveniently without having to additionally `using/import` the above packages. Please see the `Examples` section for brief usage. Note that only the variables whose name is registered as `u` in a `JuMP` model uncertainty set will be recognized as the uncertainty variables unless there is only one registered variable name (or all variables are anonymous).

# Keywords

  * `MPsolver::Module = HiGHS`: The solver for the master problem (`MP`). It should be chosen based on the tpyes of `Sx` and `Sy`. Generally, it should be an solver that supports mixed integer linear program (MILP) if `Sx` or `Sy` is a mixed integer space.
  * `SPsolver::Module = HiGHS`: The solver for the sub-problem (`SP`) in the KKT condition based reformulation form (both the feasiblity oracle and the optimality oracle). Since the sub-problem oracles are linearized reformulations based on big-M method, their solver should at least be an MILP solver, if `U` is just a polyhedral uncertainty set.
  * `ϵ::Real = 1e-5`: The overall absolute stopping criteria of the Extended CCG method. It's also used as the tolorence in the feasiblity oracle for which if the objective value of the oracle is not less than `ϵ` we then think the current `x` is infeasible.
  * `BigM::Real = 1e5`: The big-M value of `SP` in its big-M method based linearized reformulation (both the feasiblity oracle and the optimality oracle). Note that if a tight bound on big-M can be analytically obtained, a better performance of the algorithm can be achieved.
  * `verbose::Bool = true`: The switch that controls the output of the solution process details.

# Returns

This function will return a `Tuple{Vector{Real}, Real, Integer}` whose entries are in order:

  * `x::Vector{Real}`: the optimal solution to the first stage decision variable `x`.
  * `objv::Real`: the optimal objective value of the two-stage robust optimization problem.
  * `k::Integer`: the total number of iterations when the solution process terminates.

# Examples

```julia
using MKLTwoStageRO
```

### Case-1:

```julia
c = [2]; b = [1];
A = [0;;]; d = [0]; 
G = [1;;]; h = [0]; E = [-1;;]; M = [-1;;];
Sy = [ZeroOne()]; Sx = [Rplus()]; 
# Call the function with a JuMP `Model` type uncertianty set:
UncMod = Model()
@variable(UncMod, 0 <= δ <= 1)
y, objv = SolveTwoStageRO_ECCG(c, b, A, d, G, h, E, M, Sy, Sx, UncMod)
# # Call the function with a `Polyhedron` type uncertianty set:
# UncSet = polyhedron(HalfSpace([1], 1) ∩ HalfSpace([-1], 0))
# y, objv = SolveTwoStageRO_CCG(c, b, A, d, G, h, E, M, Sy, Sx, UncSet)
```

### Case-2:

```julia
c = [1, 2]; b = [3];
A = [4 5]; d = [6]; 
G = [1;;]; h = [2]; E = [-3 -4]; M = [-5 -6];
Sx = [Rplus()]; Sy = [Rplus(), ZeroOne()];
# Call the function with a JuMP `Model` type uncertianty set:
UncMod = Model()
u0 = [0, 0]
@variable(UncMod, u[1:2])
@variable(UncMod, -1 <= δ[1:2] <= 1)
@constraint(UncMod, u == u0 + δ)
y, objv = SolveTwoStageRO_ECCG(c, b, A, d, G, h, E, M, Sy, Sx, UncMod)
# # Call the function with a `Polyhedron` type uncertianty set:
# UncSet = polyhedron(UncMod, CDDLib.Library(:exact))
# ind_δ = ind_of_var(UncMod, "δ")
# UncSet = eliminate(UncSet, ind_δ)
# y, objv = SolveTwoStageRO_CCG(c, b, A, d, G, h, E, M, Sy, Sx, UncSet)
```

# References

1. Bertsimas, D., & Shtern, S. (2018). A scalable algorithm for two-stage adaptive linear optimization. arXiv preprint arXiv:1807.02812.
