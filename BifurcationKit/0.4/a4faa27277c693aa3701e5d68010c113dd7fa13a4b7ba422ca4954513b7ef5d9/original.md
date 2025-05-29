```julia
struct BifFunction{Tf, TFinp, Tdf, Tdfad, Tj, Tjad, TJinp, Td2f, Td2fc, Td3f, Td3fc, Tδ, Tjet} <: BifurcationKit.AbstractBifurcationFunction
```

Structure to hold the vector field and its derivatives. It should rarely be called directly. Also, in essence, it is very close to `SciMLBase.ODEFunction`.

## Fields

  * `F::Any`: Vector field. Function of type out-of-place `result = f(x, p)` or inplace `f(result, x, p)`. For type stability, the types of `x` and `result` should match
  * `F!::Any`: Same as F but inplace with signature F!(result, x, p)
  * `dF::Any`: Differential of `F` with respect to `x`, signature `dF(x,p,dx)`
  * `dFad::Any`: Adjoint of the Differential of `F` with respect to `x`, signature `dFad(x,p,dx)`
  * `J::Any`: Jacobian of `F` at `(x, p)`. It can assume three forms.         1. Either `J` is a function and `J(x, p)` returns a `::AbstractMatrix`. In this case, the default arguments of `contparams::ContinuationPar` will make `continuation` work.         2. Or `J` is a function and `J(x, p)` returns a function taking one argument `dx` and returning `dr` of the same type as `dx`. In our notation, `dr = J * dx`. In this case, the default parameters of `contparams::ContinuationPar` will not work and you have to use a Matrix Free linear solver, for example `GMRESIterativeSolvers`,         3. Or `J` is a function and `J(x, p)` returns a variable `j` which can assume any type. Then, you must implement a linear solver `ls` as a composite type, subtype of `AbstractLinearSolver` which is called like `ls(j, rhs)` and which returns the solution of the jacobian linear system. See for example `examples/SH2d-fronts-cuda.jl`. This linear solver is passed to `NewtonPar(linsolver = ls)` which itself passed to `ContinuationPar`. Similarly, you have to implement an eigensolver `eig` as a composite type, subtype of `AbstractEigenSolver`.
  * `Jᵗ::Any`: jacobian adjoint, it should be implemented in an efficient manner. For matrix-free methods, `transpose` is not readily available and the user must provide a dedicated method. In the case of sparse based jacobian, `Jᵗ` should not be passed as it is computed internally more efficiently, i.e. it avoids recomputing the jacobian as it would be if you pass `Jᵗ = (x, p) -> transpose(dF(x, p))`.
  * `J!::Any`: Inplace jacobian
  * `d2F::Any`: Second Differential of `F` with respect to `x`, signature `d2F(x,p,dx1,dx2)`
  * `d3F::Any`: Third Differential of `F` with respect to `x`, signature `d3F(x,p,dx1,dx2,dx3)`
  * `d2Fc::Any`: [internal] Second Differential of `F` with respect to `x` which accept complex vectors dxi
  * `d3Fc::Any`: [internal] Third Differential of `F` with respect to `x` which accept complex vectors dxi
  * `isSymmetric::Bool`: Whether the jacobian is auto-adjoint.
  * `δ::Any`: used internally to compute derivatives (with finite differences), for example for normal form computation and codim 2 continuation.
  * `inplace::Bool`: optionally sets whether the function is inplace or not. You can use `in_bisection(state)` to inquire whether the current state is in bisection mode.
  * `jet::Any`: jet of the vector field

## Methods

  * `residual(pb::BifFunction, x, p)` calls `pb.F(x,p)`
  * `jacobian(pb::BifFunction, x, p)` calls `pb.J(x, p)`
  * `dF(pb::BifFunction, x, p, dx)` calls `pb.dF(x,p,dx)`
  * `R21(pb::BifFunction, x, p, dx1, dx2, dp1)` calls `pb.jet.R21(x, p, dx1, dx2, dp1)`. Same for the other jet functions.
  * etc
