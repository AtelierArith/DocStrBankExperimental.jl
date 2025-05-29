```julia
struct PDESystem <: ModelingToolkit.AbstractMultivariateSystem
```

A system of partial differential equations.

# Fields

  * `eqs`: The equations which define the PDE.
  * `bcs`: The boundary conditions.
  * `domain`: The domain for the independent variables.
  * `ivs`: The independent variables.
  * `dvs`: The dependent variables.
  * `ps`: The parameters.
  * `defaults`: The default values to use when initial conditions and/or parameters are not supplied in `ODEProblem`.

  * `connector_type`: Type of the system.

  * `systems`: The internal systems. These are required to have unique names.

  * `analytic`: A vector of explicit symbolic expressions for the analytic solutions of each dependent variable. e.g. `analytic = [u(t, x) ~ a*sin(c*t) * cos(k*x)]`.

  * `analytic_func`: A vector of functions for the analytic solutions of each dependent variable. Will be generated from `analytic` if not provided. Should have the same argument signature as the variable, and a `ps` argument as the last argument, which takes an indexable of parameter values in the order you specified them in `ps`. e.g. `analytic_func = [u(t, x) => (ps, t, x) -> ps[1]*sin(ps[2]*t) * cos(ps[3]*x)]`.

  * `name`: The name of the system.

  * `description`: A description of the system.

  * `metadata`: Metadata for the system, to be used by downstream packages.

  * `gui_metadata`: Metadata for MTK GUI.

# Example

```julia
using ModelingToolkit

@parameters x t
@variables u(..)
Dxx = Differential(x)^2
Dtt = Differential(t)^2
Dt = Differential(t)

#2D PDE
C=1
eq  = Dtt(u(t,x)) ~ C^2*Dxx(u(t,x))

# Initial and boundary conditions
bcs = [u(t,0) ~ 0.,# for all t > 0
       u(t,1) ~ 0.,# for all t > 0
       u(0,x) ~ x*(1. - x), #for all 0 < x < 1
       Dt(u(0,x)) ~ 0. ] #for all  0 < x < 1]

# Space and time domains
domains = [t ∈ (0.0,1.0),
           x ∈ (0.0,1.0)]

@named pde_system = PDESystem(eq,bcs,domains,[t,x],[u])
```
