```
SolveTwoStageRO_CCG(args...; kwargs...)
```

Solve the following two-stage robust optimization problems using (nested) column-and-constraint generation (C&CG) method (`Ref.1-2`):

```formulation
Min_y c' * y + Max_{u ∈ U} Min_{x ∈ F(y, u)} b' * x

Subject to:

    A * y ≥ d, y ∈ Sy

    F(y, u) = {x ∈ Sx: G * x ≥ h - E * y - M * u}

    U is the uncertainty set
```

where `Sy` and `Sx` are allowed to be nonnegative real-valued spaces or nonnegative mixed integer spaces.

P.S. We hope the following mild assumptions hold (`Ref.1-2`):

  * The Relatively Complete Recourse assumption when `Sx` is a nonnegative real-valued space, i.e., the second-stage decision problem (which is a linear program) is feasible for any given `y` and `u`.
  * When `Sx` is a nonnegative mixed integer space, it has at least one real-valued dimension, i.e., the mixed integer programming recourse problem has at least one continuous recourse variable.
  * The Extended Relatively Complete Recourse property when `Sx` is a nonnegative mixed integer space, i.e., the problem obtained by fixing `y`, `u` and the integer part of `x` (which is a linear program) is always feasible and bounded.
  * When `Sx` is a nonnegative mixed integer space, the feasible set of discrete recouse variables (i.e., the integer part of `x`) is bounded.

# Arguments

  * `c::AbstractVector{<:Real}`: It should be a vector. A degenerate scalar `c` should be converted into a vector form first, e.g., `c = [2]`.
  * `b::AbstractVector{<:Real}`: It should be a vector. A degenerate scalar `b` should be converted into a vector form first, e.g., `b = [1]`.
  * `A::AbstractMatrix{<:Real}`: It should be a matrix. A degenerate vector or scalar `A` should be converted into a matrix form first, e.g., `A = [1 2]`, `A = [1; 2;;]` or `A = [0;;]`.
  * `d::AbstractVector{<:Real}`: It should be a vector. A degenerate scalar `d` should be converted into a vector form first, e.g., `d = [0]`.
  * `G::AbstractMatrix{<:Real}`: It should be a matrix. A degenerate vector or scalar `G` should be converted into a matrix form first, e.g., `G = [1 2]`, `G = [1; 2;;]` or `G = [1;;]`.
  * `h::AbstractVector{<:Real}`: It should be a vector. A degenerate scalar `h` should be converted into a vector form first, e.g., `h = [0]`.
  * `E::AbstractMatrix{<:Real}`: It should be a matrix. A degenerate vector or scalar `E` should be converted into a matrix form first, e.g., `E = [1 2]`, `E = [1; 2;;]` or `E = [-1;;]`.
  * `M::AbstractMatrix{<:Real}`: It should be a matrix. A degenerate vector or scalar `M` should be converted into a matrix form first, e.g., `M = [1 2]`, `M = [1; 2;;]` or `M = [-1;;]`.
  * `Sy::Vector{<:BasicDomain}`: It is allowed to be a nonnegative real-valued space or a nonnegative mixed integer space. It should be constructed as a vector consisting of (a mixture of) instances of the following three basic data types: `Rplus`, `ZeroOne` and `Zplus`. E.g., `Sy = [ZeroOne()]` denotes an one-dimensional binary space `{0, 1}` and `Sy = [Rplus(2), Zplus(3)]` denotes a five-dimensianal nonnegative mixed integer space `ℝ₊² × ℤ₊³`. Note that the latter is equivalent to `Sy = [fill(Rplus(), 2), fill(Zplus(), 3)]`.
  * `Sx::Vector{<:BasicDomain}`: It is allowed to be a nonnegative real-valued space or a nonnegative mixed integer space. If it is the former, the algorithm (C&CG) from `Ref.1` will be called; if it is the latter, the algorithm (Nested C&CG) from `Ref.2` will be called. It should be constructed as a vector consisting of (a mixture of) instances of the following three basic data types: `Rplus`, `ZeroOne` and `Zplus`. The construction method is the same as `Sy`.
  * `U::Union{Model, Polyhedron}`: The uncertainty set is allowed to be constructed as a `Model` using package `JuMP.jl` or a `Polyhedron` using package `Polyhedra.jl`. This package has integrated some neccessary functions from `JuMP.jl`, `Polyhedra.jl` and some other related packages, which allows the user to model the uncertainty set conveniently without having to additionally `using/import` the above packages. Please see the `Examples` section for brief usage. Note that only the variables whose name is registered as `u` in a `JuMP` model uncertainty set will be recognized as the uncertainty variables unless there is only one registered variable name (or all variables are anonymous).

# Keywords

  * `MPsolver::Module = HiGHS`: The solver for the master problem (`MP`). It should be chosen based on the tpyes of `Sy` and `Sx`. Generally, it should be an solver that supports mixed integer linear program (MILP) if `Sy` or `Sx` is a mixed integer space.
  * `SP1solver::Module = HiGHS`: The solver for the sub-problem in the KKT condition based reformulation (Bi/Tri-Equivalent I) form (`SP1`). Since `SP1` is a linearized reformulation based on big-M method, its solver should at least be an MILP solver, if `U` is just a polyhedral uncertainty set.
  * `SP2solver::Module = Ipopt`: This keyword argument is only available when `Sx` is a nonnegative real-valued space. It's the solver for the sub-problem in the strong duality based reformulation form (`SP2`). The function will always try to solve `SP1` first, and then move on to `SP2` if it fails. Since `SP2` is at least a bilinear optimization problem when `U` is a polyhedron, a solver that is tailored to this or roughly one that supports non-convex quadratic program (QP) is neccessary.
  * `SP2solver_max_iter::Integer = 10000`: This keyword argument is only available when `Sx` is a nonnegative real-valued space. It's the maximum limitation of iterations for `SP2solver` to solve `SP2`.
  * `SP2_MPsolver::Module = Ipopt`: This keyword argument is only available when `Sx` is a nonnegative mixed integer space. It's the solver for the master problem of the sub-problem in the strong duality based reformulation (Bi/Tri-Equivalent II) form (`SP2`). The function will always try to solve `SP1` first, and then move on to `SP2` if it fails. Since the master problem of `SP2` contains quadratic constraints even when `U` is just a polyhedral uncertainty set, an efficient solver that supports quadratically-constrained quadratic program (QCQP) is neccessary.
  * `SP2_MPsolver_max_iter::Integer = 10000`: This keyword argument is only available when `Sx` is a nonnegative mixed integer space. It's the maximum limitation of iterations for `SP2_MPsolver` to solve the master problem of `SP2`.
  * `SP2_SPsolver::Module = HiGHS`: This keyword argument is only available when `Sx` is a nonnegative mixed integer space.  It's the solver for the sub-problem of the sub-problem in the strong duality based reformulation (Bi/Tri-Equivalent II) form (`SP2`). The function will always try to solve `SP1` first, and then move on to `SP2` if it fails. The solver for the sub-problem of `SP2` only depends on the tpye of `Sx`, so it should be an MILP solver beacause of the mixed integer feature of `Sx`.
  * `ϵ::Real = 1e-5`: The overall absolute stopping criteria of the (nested) C&CG method. If the internal quadratic programming solver is active, it's also the tolorence of it.
  * `BigM::Real = 1e5`: The big-M value of `SP1` in its big-M method based linearized reformulation. Note that if a tight bound on big-M can be analytically obtained, a better performance of the algorithm can be achieved.
  * `verbose::Bool = true`: The switch that controls the output of the solution process details.

# Returns

This function will return a `Tuple{Vector{Real}, Real, Integer}` whose entries are in order:

  * `y::Vector{Real}`: the optimal solution to the first stage decision variable `y`.
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
y, objv = SolveTwoStageRO_CCG(c, b, A, d, G, h, E, M, Sy, Sx, UncMod) 
# Call the function with a `Polyhedron` type uncertianty set:
UncSet = polyhedron(HalfSpace([1], 1) ∩ HalfSpace([-1], 0))
y, objv = SolveTwoStageRO_CCG(c, b, A, d, G, h, E, M, Sy, Sx, UncSet)
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
y, objv = SolveTwoStageRO_CCG(c, b, A, d, G, h, E, M, Sy, Sx, UncMod)
# Call the function with a `Polyhedron` type uncertianty set:
UncSet = polyhedron(UncMod, CDDLib.Library(:exact))
ind_δ = ind_of_var(UncMod, "δ")
UncSet = eliminate(UncSet, ind_δ)
y, objv = SolveTwoStageRO_CCG(c, b, A, d, G, h, E, M, Sy, Sx, UncSet)
```

### Case-3:

```julia
c = [1]; b = [2; 3];
A = [4;;]; d = [5];
G = [6 7]; h = [8]; E = [10;;]; M = [9;;];
Sy = [Rplus()]; Sx = [Rplus(); ZeroOne()];
# Call the function with a JuMP `Model` type uncertianty set:
UncMod = Model()
@variable(UncMod, u)
δ = @expression(UncMod, 2u - 1)
@constraint(UncMod, -1 <= δ <= 1)
y, objv = SolveTwoStageRO_CCG(c, b, A, d, G, h, E, M, Sy, Sx, UncMod)
# Call the function with a `Polyhedron` type uncertianty set:
UncSet = polyhedron(convexhull([0], [1]))
y, objv = SolveTwoStageRO_CCG(c, b, A, d, G, h, E, M, Sy, Sx, UncSet)
```

# References

1. Zeng, B., & Zhao, L. (2013). Solving two-stage robust optimization problems using a column-and-constraint generation method. Operations Research Letters, 41(5), 457-461.
2. Zhao, L., & Zeng, B. (2012). An exact algorithm for two-stage robust optimization with mixed integer recourse problems. submitted, available on Optimization-Online. org.
