```julia
struct BorderingBLS{S<:Union{Nothing, BifurcationKit.AbstractLinearSolver}, Ttol} <: BifurcationKit.AbstractBorderedLinearSolver
```

This struct is used to provide the bordered linear solver based on the Bordering Method. Using the options, you can trigger a sequence of Bordering reductions to meet a precision.

# Reference

This is the solver BEC + k in Govaerts, W. “Stable Solvers and Block Elimination for Bordered Systems.” SIAM Journal on Matrix Analysis and Applications 12, no. 3 (July 1, 1991): 469–83. https://doi.org/10.1137/0612034.

  * `solver::Union{Nothing, BifurcationKit.AbstractLinearSolver}`: Linear solver for the Bordering method. Default: nothing
  * `tol::Any`: Tolerance for checking precision Default: 1.0e-12
  * `check_precision::Bool`: Check precision of the linear solve? Default: true
  * `k::Int64`: Number of recursions to achieve tolerance Default: 1

# Constructors

  * there is a  simple constructor `BorderingBLS(ls)` where `ls` is a linear solver, for example `ls = DefaultLS()`
  * you can use keyword argument to create such solver, for example `BorderingBLS(solver = DefaultLS(), tol = 1e-4)`
