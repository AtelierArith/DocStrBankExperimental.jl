`change_simulation_stop_criteria(m::ContinuousTimeModel, isabsorbing_func::Symbol)`

Change the simulation of the model `m` by adding a stop criteria based on the function named `isabsorbing_func::Symbol`. `isabsorbing_func` must have the type signature `isabsorbing_func(p::Vector{Float64}, x::Vector{Int})` where `p` is the parameter vector of the model and `x` a state (not an observed state) of the model.
