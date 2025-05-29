Defines an fractional ordinary differential equation (FODE) problem.

## Mathematical Specification of an FODE problem

To define an FODE Problem, you simply need to given the function $f$ and the initial condition $u_0$  which define an FODE:

$$
\frac{du^\alpha}{d^{\alpha}t} = f(u,p,t)
$$

There are two different ways of specifying `f`:

  * `f(du,u,p,t)`: in-place. Memory-efficient when avoiding allocations. Best option for most cases unless mutation is not allowed.
  * `f(u,p,t)`: returning `du`. Less memory-efficient way, particularly suitable when mutation is not allowed (e.g. with certain automatic differentiation packages such as Zygote).
  * `order`: the fractional order of the differential equations, commensurate and non-commensurate is both supported. -`u₀` should be an AbstractArray (or number) whose geometry matches the desired geometry of `u`. Note that we are not limited to numbers or vectors for `u₀`; one is allowed to provide `u₀` as arbitrary matrices / higher dimension tensors as well.

## Problem Type

### Constructors

`FODEProblem` can be constructed by first building an `ODEFunction` or by simply passing the FODE right-hand side to the constructor. The constructors are:

  * `FODEProblem(f::ODEFunction,u0,tspan,p=NullParameters();kwargs...)`
  * `FODEProblem{isinplace,specialize}(f,u0,tspan,p=NullParameters();kwargs...)` : Defines the FODE with the specified functions. `isinplace` optionally sets whether the function is inplace or not. This is determined automatically, but not inferred. `specialize` optionally controls the specialization level. See the [specialization levels section of the SciMLBase documentation](https://docs.sciml.ai/SciMLBase/stable/interfaces/Problems/#Specialization-Levels) for more details. The default is `AutoSpecialize`.

For more details on the in-place and specialization controls, see the ODEFunction documentation.

Parameters are optional, and if not given, then a `NullParameters()` singleton will be used which will throw nice errors if you try to index non-existent parameters. Any extra keyword arguments are passed on to the solvers. For example, if you set a `callback` in the problem, then that `callback` will be added in every solve call.

For specifying Jacobians and mass matrices, see the `ODEFunction` documentation.

### Fields

  * `f`: The function in the ODE.
  * `order`: The order of the FODE.
  * `u0`: The initial condition.
  * `tspan`: The timespan for the problem.
  * `p`: The parameters.
  * `kwargs`: The keyword arguments passed onto the solves.

## Example Problem

```julia
using SciMLBase
function lorenz!(du, u, p, t)
    du[1] = 10.0(u[2] - u[1])
    du[2] = u[1] * (28.0 - u[3]) - u[2]
    du[3] = u[1] * u[2] - (8 / 3) * u[3]
end
order = [0.96; 0.96; 0.96]
u0 = [1.0; 0.0; 0.0]
tspan = (0.0, 100.0)
prob = FODEProblem(lorenz!, u0, tspan)

# Test that it worked
using FractionalDiffEq
sol = solve(prob, PIEX())
using Plots;
plot(sol, vars = (1, 2, 3));
```
