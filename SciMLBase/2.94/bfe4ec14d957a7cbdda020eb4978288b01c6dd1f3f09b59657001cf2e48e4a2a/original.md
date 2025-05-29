```julia
struct OptimizationFunction{iip, AD, F, G, FG, H, FGH, HV, C, CJ, CJV, CVJ, CH, HP, CJP, CHP, O, EX, CEX, SYS, LH, LHP, HCV, CJCV, CHCV, LHCV, ID} <: SciMLBase.AbstractOptimizationFunction{iip}
```

A representation of an objective function `f`, defined by:

$$
\min_{u} f(u,p)
$$

and all of its related functions, such as the gradient of `f`, its Hessian, and more. For all cases, `u` is the state which in this case are the optimization variables and `p` are the fixed parameters or data.

## Constructor

```julia
OptimizationFunction{iip}(f, adtype::AbstractADType = NoAD();
                          grad = nothing, hess = nothing, hv = nothing,
                          cons = nothing, cons_j = nothing, cons_jvp = nothing,
                          cons_vjp = nothing, cons_h = nothing,
                          hess_prototype = nothing,
                          cons_jac_prototype = nothing,
                          cons_hess_prototype = nothing,
                          observed = __has_observed(f) ? f.observed : DEFAULT_OBSERVED_NO_TIME,
                          lag_h = nothing,
                          hess_colorvec = __has_colorvec(f) ? f.colorvec : nothing,
                          cons_jac_colorvec = __has_colorvec(f) ? f.colorvec : nothing,
                          cons_hess_colorvec = __has_colorvec(f) ? f.colorvec : nothing,
                          lag_hess_colorvec = nothing,
                          sys = __has_sys(f) ? f.sys : nothing)
```

## Positional Arguments

  * `f(u,p)`: the function to optimize. `u` are the optimization variables and `p` are fixed parameters or data used in the objective, even if no such parameters are used in the objective it should be an argument in the function. For minibatching `p` can be used to pass in a minibatch, take a look at the tutorial [here](https://docs.sciml.ai/Optimization/stable/tutorials/minibatch/) to see how to do it. This should return a scalar, the loss value, as the return output.
  * `adtype`: see the Defining Optimization Functions via AD section below.

## Keyword Arguments

  * `grad(G,u,p)` or `G=grad(u,p)`: the gradient of `f` with respect to `u`.
  * `hess(H,u,p)` or `H=hess(u,p)`: the Hessian of `f` with respect to `u`.
  * `hv(Hv,u,v,p)` or `Hv=hv(u,v,p)`: the Hessian-vector product $(d^2 f / du^2) v$.
  * `cons(res,u,p)` or `res=cons(u,p)` : the constraints function, should mutate the passed `res` array   with value of the `i`th constraint, evaluated at the current values of variables   inside the optimization routine. This takes just the function evaluations   and the equality or inequality assertion is applied by the solver based on the constraint   bounds passed as `lcons` and `ucons` to [`OptimizationProblem`](@ref), in case of equality   constraints `lcons` and `ucons` should be passed equal values.
  * `cons_j(J,u,p)` or `J=cons_j(u,p)`: the Jacobian of the constraints.
  * `cons_jvp(Jv,u,v,p)` or `Jv=cons_jvp(u,v,p)`: the Jacobian-vector product of the constraints.
  * `cons_vjp(Jv,u,v,p)` or `Jv=cons_vjp(u,v,p)`: the Jacobian-vector product of the constraints.
  * `cons_h(H,u,p)` or `H=cons_h(u,p)`: the Hessian of the constraints, provided as  an array of Hessians with `res[i]` being the Hessian with respect to the `i`th output on `cons`.
  * `hess_prototype`: a prototype matrix matching the type that matches the Hessian. For example, if the Hessian is tridiagonal, then an appropriately sized `Hessian` matrix can be used as the prototype and optimization solvers will specialize on this structure where possible. Non-structured sparsity patterns should use a `SparseMatrixCSC` with a correct sparsity pattern for the Hessian. The default is `nothing`, which means a dense Hessian.
  * `cons_jac_prototype`: a prototype matrix matching the type that matches the constraint Jacobian. The default is `nothing`, which means a dense constraint Jacobian.
  * `cons_hess_prototype`: a prototype matrix matching the type that matches the constraint Hessian. This is defined as an array of matrices, where `hess[i]` is the Hessian w.r.t. the `i`th output. For example, if the Hessian is sparse, then `hess` is a `Vector{SparseMatrixCSC}`. The default is `nothing`, which means a dense constraint Hessian.
  * `lag_h(res,u,sigma,mu,p)` or `res=lag_h(u,sigma,mu,p)`: the Hessian of the Lagrangian, where `sigma` is a multiplier of the cost function and `mu` are the Lagrange multipliers multiplying the constraints. This can be provided instead of `hess` and `cons_h` to solvers that directly use the Hessian of the Lagrangian.
  * `hess_colorvec`: a color vector according to the SparseDiffTools.jl definition for the sparsity pattern of the `hess_prototype`. This specializes the Hessian construction when using finite differences and automatic differentiation to be computed in an accelerated manner based on the sparsity pattern. Defaults to `nothing`, which means a color vector will be internally computed on demand when required. The cost of this operation is highly dependent on the sparsity pattern.
  * `cons_jac_colorvec`: a color vector according to the SparseDiffTools.jl definition for the sparsity pattern of the `cons_jac_prototype`.
  * `cons_hess_colorvec`: an array of color vector according to the SparseDiffTools.jl definition for the sparsity pattern of the `cons_hess_prototype`.

When [Symbolic Problem Building with ModelingToolkit](https://docs.sciml.ai/Optimization/stable/tutorials/symbolic/) interface is used the following arguments are also relevant:

  * `observed`: an algebraic combination of optimization variables that is of interest to the user   which will be available in the solution. This can be single or multiple expressions.
  * `sys`: field that stores the `OptimizationSystem`.

## Defining Optimization Functions via AD

While using the keyword arguments gives the user control over defining all of the possible functions, the simplest way to handle the generation of an `OptimizationFunction` is by specifying an option from ADTypes.jl which lets the user choose the Automatic Differentiation backend to use for automatically filling in all of the extra functions. For example,

```julia
OptimizationFunction(f,AutoForwardDiff())
```

will use [ForwardDiff.jl](https://github.com/JuliaDiff/ForwardDiff.jl) to define all of the necessary functions. Note that if any functions are defined directly, the auto-AD definition does not overwrite the user's choice.

Each of the AD-based constructors are documented separately via their own dispatches below in the [Automatic Differentiation Construction Choice Recommendations](@ref ad) section.

## iip: In-Place vs Out-Of-Place

For more details on this argument, see the ODEFunction documentation.

## specialize: Controlling Compilation and Specialization

For more details on this argument, see the ODEFunction documentation.

## Fields

The fields of the OptimizationFunction type directly match the names of the inputs.
