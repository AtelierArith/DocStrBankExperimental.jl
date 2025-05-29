```
make_ODEProblem(metabolic_pathway, init_cond, tspan, params)
```

Construct an ODEProblem for simulating a metabolic pathway.

# Arguments

  * `metabolic_pathway::MetabolicPathway`: A structure that defines the metabolic pathway, including the substrates, products, and related reaction details.
  * `init_cond::LArray`: The initial conditions for the metabolites.
  * `tspan::Tuple{<:Number, <:Number}`: A tuple specifying the start and end times for the simulation.
  * `params::LArray`: Parameters used in the metabolic reactions (e.g., kinetic constants).

# Returns

An `ODEProblem` instance that encapsulates the differential equations governing the metabolic pathway. This problem can be solved using ODE solvers from SciMLBase.

# Details

The returned ODEProblem uses `metabolicpathway_odes!` to compute the time evolution of metabolite concentrations by adjusting their rates based on enzyme kinetics defined in `enzyme_rates`. Ensure that `metabolic_pathway`, `init_cond`, and `params` have matching entries for substrates, products, and parameters for correct simulation.

# Example

```julia
using CellMetabolismBase
using DifferentialEquations

metab_path = MetabolicPathway(...)
init_cond = LArray(...)
tspan = (0.0, 1e8)
params = LArray(...)
prob = make_ODEProblem(metab_path, init_cond, tspan, params)
sol = solve(prob, RadauIIA9(), abstol=1e-15, reltol=1e-8)
```
