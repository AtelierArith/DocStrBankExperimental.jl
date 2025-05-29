```
setup(parametrizedSPAC::SPAC;
    requested_tspan = nothing,
    soil_output_depths_m::Vector = zeros(Float64, 0))
```

Takes the definition of SPAC model and discretize to a system of ODEs that can be solved by the package DifferentialEquations.jl

If needed, the computational grid of the soil is refined to output values at specific depths, e.g. by doing `setup(SPAC; soil_output_depths_m = [-0.35, -0.42, -0.48, -1.05])`.

The argument `requested_tspan` is a tuple defining the duration of the simulation either with a start- and an end-day relative to the reference date: `setup(SPAC; requested_tspan = (0,150))`. or alternatively as a tuple of 2 DataTime's. Note that the reference date given by the `SPAC.reference_date` refers to the day 0. Further note that it is possible to provide a tspan not starting at 0, e.g. (120,150). In that case, initial conditions are applied tspan[1], but atmospheric forcing is correctly taken into account.
