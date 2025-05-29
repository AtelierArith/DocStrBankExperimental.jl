```
analyze(sim_inst::SobolSimulationInstance, model_output::AbstractArray{<:Number, N}; 
        num_resamples::Union{Nothing, Int} = 1_000, conf_level::Union{Nothing, Number} = 0.95, 
        N_override::Union{Nothing, Int}=nothing, progress_meter::Bool = true) where N
```

Analyze the results for `sim_inst` with intput `model_input` and output `model_output`  and return sensitivity analysis metrics as defined by GlobalSensitivityAnalysis package and  type parameterization of the `sim_inst` ie. Sobol Method.
