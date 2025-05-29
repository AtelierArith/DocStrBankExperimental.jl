Defines a fractional delay differential equation (FDDE) problem.

## Mathematical Specification of an FDDE problem

To define an FDDE problem, you simply need to given the function $f$, the history function $ϕ$, the fractional order $α$, the delay $τ$ and the initial condition $u₀$  which define an FDDE:

$$
D^\alpha_t y(t)=f(t,y(t),y(t-τ)),t ≥ 0
$$

$$
y(t)=ϕ(t), t ≤ 0
$$

There are two different ways of specifying `f`:

  * `f(du,u,h,p,t)`: The function describing fractional delay differential equations.
  * `f(u,h,p,t)`: returning `du`. Less memory-efficient way, particularly suitable when mutation is not allowed (e.g. with certain automatic differentiation packages such as Zygote).
  * `ϕ`: History function
  * `α`: The fractional order of the differential equations, commensurate and non-commensurate is both supported.
  * `τ`: The time delay of the differential equations.

## Problem Type

### Constructors

`FODEProblem` can be constructed by first building an `ODEFunction` or by simply passing the FODE right-hand side to the constructor. The constructors are:

  * `FDDEProblem(f::ODEFunction,order,u0,ϕ,tspan,p=NullParameters();kwargs...)`
  * `FDDEProblem{isinplace,specialize}(f,order,u0,ϕ,tspan,p=NullParameters();kwargs...)` : Defines the FODE with the specified functions. `isinplace` optionally sets whether the function is inplace or not. This is determined automatically, but not inferred. `specialize` optionally controls the specialization level. See the [specialization levels section of the SciMLBase documentation](https://docs.sciml.ai/SciMLBase/stable/interfaces/Problems/#Specialization-Levels) for more details. The default is `AutoSpecialize`.

For more details on the in-place and specialization controls, see the ODEFunction documentation.

Parameters are optional, and if not given, then a `NullParameters()` singleton will be used which will throw nice errors if you try to index non-existent parameters. Any extra keyword arguments are passed on to the solvers. For example, if you set a `callback` in the problem, then that `callback` will be added in every solve call.

For specifying Jacobians and mass matrices, see the `ODEFunction` documentation.

### Fields

  * `f`: The function in the FDDE.
  * `ϕ`: The history function in the FDDE.
  * `order`: The order of the FDDE.
  * `τ`: The time delay of the FDDE.
  * `tspan`: The timespan for the problem.
  * `p`: The parameters.
  * `kwargs`: The keyword arguments passed onto the solves.

## Example Problem

```julia
function ϕ(p, t)
    if t == 0
        return 19.00001
    else
        return 19.0
    end
end
function f(y, ϕ, p, t)
    return 3.5 * y * (1 - ϕ / 19)
end
τ = [0.8]
order = 0.97
u0 = 19.00001
tspan = (0.0, 2.0)
dt = 0.5
prob = FDDEProblem(f, order, u0, ϕ, constant_lags = τ, tspan)
sol = solve(prob, DelayPIEX(), dt = dt)
```
