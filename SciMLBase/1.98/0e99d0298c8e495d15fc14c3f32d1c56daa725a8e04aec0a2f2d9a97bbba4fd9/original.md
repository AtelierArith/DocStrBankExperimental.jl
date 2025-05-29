```
OptimizationFunction{iip,AD,F,G,H,HV,C,CJ,CH,HP,CJP,CHP,S,S2,HCV,CJCV,CHCV} <: AbstractOptimizationFunction{iip,specialize}
```

A representation of an optimization of an objective function `f`, defined by:

$$
\min_{u} f(u,p)
$$

and all of its related functions, such as the gradient of `f`, its Hessian, and more. For all cases, `u` is the state and `p` are the parameters.

## Constructor

```julia
OptimizationFunction{iip}(f, adtype::AbstractADType = NoAD();
                          grad = nothing, hess = nothing, hv = nothing,
                          cons = nothing, cons_j = nothing, cons_h = nothing,
                          lag_h = nothing,
                          hess_prototype = nothing, cons_jac_prototype = __has_jac_prototype(f) ? f.jac_prototype : nothing,
                          cons_hess_prototype = nothing,
                          lag_hess_prototype = nothing,
                          syms = __has_syms(f) ? f.syms : nothing,
                          paramsyms = __has_paramsyms(f) ? f.paramsyms : nothing,
                          observed = __has_observed(f) ? f.observed : DEFAULT_OBSERVED_NO_TIME,
                          hess_colorvec = __has_colorvec(f) ? f.colorvec : nothing,
                          cons_jac_colorvec = __has_colorvec(f) ? f.colorvec : nothing,
                          cons_hess_colorvec = __has_colorvec(f) ? f.colorvec : nothing,
                          lag_hess_colorvec = nothing,
                          sys = __has_sys(f) ? f.sys : nothing)
```

## Positional Arguments

  * `f(u,p)`: the function to optimize. `u` are the state variables and `p` are the hyperparameters of the optimization. This function should return a scalar.
  * `adtype`: see the section "Defining Optimization Functions via AD"

## Keyword Arguments

  * `grad(G,u,p)` or `G=grad(u,p)`: the gradient of `f` with respect to `u`
  * `hess(H,u,p)` or `H=hess(u,p)`: the Hessian of `f` with respect to `u`
  * `hv(Hv,u,v,p)` or `Hv=hv(u,v,p)`: the Hessian-vector product $(d^2 f / du^2) v$.
  * `cons(res,x,p)` or `cons(x,p)` : the constraints function, should mutate or return a vector   with value of the `i`th constraint, evaluated at the current values of variables   inside the optimization routine. This takes just the function evaluations   and the equality or inequality assertion is applied by the solver based on the constraint   bounds passed as `lcons` and `ucons` to [`OptimizationProblem`](@ref), in case of equality   constraints `lcons` and `ucons` should be passed equal values.
  * `cons_j(res,x,p)` or `res=cons_j(x,p)`: the Jacobian of the constraints.
  * `cons_h(res,x,p)` or `res=cons_h(x,p)`: the Hessian of the constraints, provided as  an array of Hessians, with `res[i]` being the Hessian with respect to the `i`th output on `cons`.
  * `lag_h(res,x,sigma,mu,p)` or `res=lag_h(x,sigma,mu,p)`: the Hessian of the Lagrangian,   where `sigma` is a multiplier of the cost function and `mu` are the Lagrange multipliers   multiplying the constraints. This can be provided instead of `hess` and `cons_h`   to solvers that directly use the Hessian of the Lagrangian.
  * `paramjac(pJ,u,p)`: returns the parameter Jacobian $df/dp$.
  * `hess_prototype`: a prototype matrix matching the type that matches the Hessian. For example, if the Hessian is tridiagonal, then an appropriately sized `Hessian` matrix can be used as the prototype and integrators will specialize on this structure where possible. Non-structured sparsity patterns should use a `SparseMatrixCSC` with a correct sparsity pattern for the Hessian. The default is `nothing`, which means a dense Hessian.
  * `cons_jac_prototype`: a prototype matrix matching the type that matches the constraint Jacobian. The default is `nothing`, which means a dense constraint Jacobian.
  * `cons_hess_prototype`: a prototype matrix matching the type that matches the constraint Hessian. This is defined as an array of matrices, where `hess[i]` is the Hessian w.r.t. the `i`th output. For example, if the Hessian is sparse, then `hess` is a `Vector{SparseMatrixCSC}`. The default is `nothing`, which means a dense constraint Hessian.
  * `syms`: the symbol names for the elements of the equation. This should match `u0` in size. For example, if `u = [0.0,1.0]` and `syms = [:x, :y]`, this will apply a canonical naming to the values, allowing `sol[:x]` in the solution and automatically naming values in plots.
  * `paramsyms`: the symbol names for the parameters of the equation. This should match `p` in size. For example, if `p = [0.0, 1.0]` and `paramsyms = [:a, :b]`, this will apply a canonical naming to the values, allowing `sol[:a]` in the solution.
  * `hess_colorvec`: a color vector according to the SparseDiffTools.jl definition for the sparsity pattern of the `hess_prototype`. This specializes the Hessian construction when using finite differences and automatic differentiation to be computed in an accelerated manner based on the sparsity pattern. Defaults to `nothing`, which means a color vector will be internally computed on demand when required. The cost of this operation is highly dependent on the sparsity pattern.
  * `cons_jac_colorvec`: a color vector according to the SparseDiffTools.jl definition for the sparsity pattern of the `cons_jac_prototype`.
  * `cons_hess_colorvec`: an array of color vector according to the SparseDiffTools.jl definition for the sparsity pattern of the `cons_hess_prototype`.

## Defining Optimization Functions Via AD

While using the keyword arguments gives the user control over defining all the possible functions, the simplest way to handle the generation of an `OptimizationFunction` is by specifying an AD type. By doing so, this will automatically fill in all the extra functions. For example,

```julia
OptimizationFunction(f,AutoZygote())
```

will use [Zygote.jl](https://docs.sciml.ai/Zygote.jl/stable/) to define all of the necessary functions. Note that if any functions are defined directly, the auto-AD definition does not overwrite the user's choice.

Each of the AD-based constructors are documented separately via their own dispatches.

## iip: In-Place vs Out-Of-Place

For more details on this argument, see the ODEFunction documentation.

## specialize: Controlling Compilation and Specialization

For more details on this argument, see the ODEFunction documentation.

## Fields

The fields of the OptimizationFunction type directly match the names of the inputs.
