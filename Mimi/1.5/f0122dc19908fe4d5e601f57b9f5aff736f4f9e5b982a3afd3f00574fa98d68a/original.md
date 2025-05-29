```
analyze(sim_inst::DeltaSimulationInstance, model_input::AbstractArray{<:Number, N1}, 
        model_output::AbstractArray{<:Number, N2}; num_resamples::Int = 1_000, 
        conf_level::Number = 0.95, N_override::Union{Nothing, Int}=nothing, 
        progress_meter::Bool = true) where {N1, N2}
```

Analyze the results for `sim_inst` with intput `model_input` and output `model_output`  and return sensitivity analysis metrics as defined by GlobalSensitivityAnalysis package and  type parameterization of the `sim_inst` ie. Delta Method.
