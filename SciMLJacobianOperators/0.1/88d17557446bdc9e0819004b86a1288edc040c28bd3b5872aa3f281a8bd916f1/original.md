```
JacobianOperator{iip, T} <: AbstractJacobianOperator{T} <: AbstractSciMLOperator{T}
```

A Jacobian Operator Provides both JVP and VJP without materializing either (if possible).

### Constructor

```julia
JacobianOperator(prob::AbstractNonlinearProblem, fu, u; jvp_autodiff = nothing,
    vjp_autodiff = nothing, skip_vjp::Val = Val(false), skip_jvp::Val = Val(false))
```

By default, the `JacobianOperator` will compute `JVP`. Use `Base.adjoint` or `Base.transpose` to switch to `VJP`.

### Computing the VJP

Computing the VJP is done according to the following rules:

  * If `f` has a `vjp` method, then we use that.
  * If `f` has a `jac` method and no `vjp_autodiff` is provided, then we use `jac * v`.
  * If `vjp_autodiff` is provided we using DifferentiationInterface.jl to compute the VJP.

### Computing the JVP

Computing the JVP is done according to the following rules:

  * If `f` has a `jvp` method, then we use that.
  * If `f` has a `jac` method and no `jvp_autodiff` is provided, then we use `v * jac`.
  * If `jvp_autodiff` is provided we using DifferentiationInterface.jl to compute the JVP.

### Special Case (Number)

For Number inputs, VJP and JVP are not distinct. Hence, if either `vjp` or `jvp` is provided, then we use that. If neither is provided, then we use `v * jac` if `jac` is provided. Finally, we use the respective autodiff methods to compute the derivative using DifferentiationInterface.jl and multiply by `v`.

### Methods Provided

!!! warning
    Currently it is expected that `p` during problem construction is same as `p` during operator evaluation. This restriction will be lifted in the future.


  * `(op::JacobianOperator)(v, u, p)`: Computes `∂f(u, p)/∂u * v` or `∂f(u, p)/∂uᵀ * v`.
  * `(op::JacobianOperator)(res, v, u, p)`: Computes `∂f(u, p)/∂u * v` or `∂f(u, p)/∂uᵀ * v` and stores the result in `res`.

See also [`VecJacOperator`](@ref) and [`JacVecOperator`](@ref).
