```
run_dice(pars;optimizer,bounds)
run_dice(;optimizer,bounds,kwargs...)
```

Run the D(R)ICE models (currently with the structure and, by default, the data of DICE2023), possibly with custom optimiser, bounds or parameters.

This function runs the DICE model and returns the results as a named tuple. Note that starting from DICEModel v0.2, a regional dimension is always present, and DICE is simply treated as RICE with a single region.  

# Function arguments

## Positional:

  * `pars`: An istance of the [`DICEParameters`](@ref) struct containing the needed parameters

## Keyword arguments:

  * `optimizer`: The optimiser to use and possibly its options. Defaults to: [`optimizer = optimizer_with_attributes(Ipopt.Optimizer,"print_level" => 0, "max_wall_time"=>10.0^20, "max_cpu_time" => 10.0^20, "max_iter" => 3000, "acceptable_tol" =>10^-6, "acceptable_iter" => 15, "acceptable_dual_inf_tol" =>10.0^10, "acceptable_constr_viol_tol" => 0.01, "acceptable_compl_inf_tol" =>0.01, "acceptable_obj_change_tol" =>10.0^20)`]. All, except the print levels, are the Ipopt defaults.
  * `bounds`: A dictionary of equality or inequality constraints. Each constraint should be specified with the variable name as key and a two-element tuple as value. The first element is either "<=", ">=" or "==", and the second element is the right-hand side of the constraint (a single value, a vector of ntimesteps length or a matrix of ntimesteps x nregions). Default: (empty dictionary). See the [source code](https://github.com/sylvaticus/DICEModel.jl/blob/main/src/DICEModel.jl) for the names of the model variables.
  * `kwargs`: Keyword arguments to override the default parameter values of DICE2023. See the documentation for the [`DICEParameters`](@ref) structure for the available model parameters.

**WARNING**: Sometimes changing a parameter doesn't lead to the expected behavior. This is because the model (in its original GAMS form that has been re-implemented in this package) performs some calibrations with the parameters, so several parameters have to be changed together. For example all the scenarios that test different discount rates don't change only the `prstp` parameter, but compute several other parameters, sometimes in a different matter than the default model, and have different calibration for initial conditions. Always check the [source code](https://github.com/sylvaticus/DICEModel.jl/blob/main/src/CoreModel.jl) to make sure that the parameter you want to change doesn't have other side effects in the model.

# Outputs

  * A named tuple containing the following fields: `solved`, `status`, `times`, `tidx`, the post_process computed values, the optimisation variables, the parameters structure (`pars`).

# Examples:

```Julia
res = run_dice()
ECO2_opt = res.ECO2
plot(res.times[1:11] .+ 2020,ECO2_opt[1:11],ylim=(0,80), title="CO₂ emissions",ylabel="GtCO₂/yr",label="C/B optimal", markershape=:circle, markercolor=:white)
```

```Julia
res_crazy = run_dice(optimizer=optimizer_with_attributes(Ipopt.Optimizer,"print_level" => 0), bounds = Dict("MIU"=>("==",1.0), "TATM"=>("<=",15), "Y" =>(">=",[fill(floatmin(Float64),10);fill(0.1,71)]), "ECO2" =>("<=",10000)), a2base = 0.01)
```

```julia
w_dev_country_priority = [1,1,1,1.5,2,2,3,3,2,5,5,5] # Utility weights by region
res_12regions_devprior = run_dice(RICE2023(;weights=w_dev_country_priority))
```

# Notes

  * The `bounds` add constraints to the problem, but do not replace hard written bounds in the model. In particular, the `miuup` parameter should be used instead for the upper limit of emission controls.
  * Bounds are always intended for the full time steps. If you need a bound for a subset of time steps (e.g. the first time step), you still need to assemble your full time array of the bound using `floatmin(Float64)` or `floatmax(Float64)` as appropriate.
  * The version with keywords arguments is a tiny wrapper (calls) the version with the parameters struct, itself built using the `DICE2023` function with the provided keyword arguments.
  * The weights used in the [`DICEParameters`](@ref) struct are exogenous, are NOT the Negishi weights. The `run_dice` function can eventually be used iteractively to look for these weights.
