```
analyze_results!(args::Dict{String,<:Any})::Dict{String,Any}
```

"output_data"に情報と統計を追加します。これには以下が含まれます。

  * `"Runtime arguments"`: `args["raw_args"]`からコピー
  * `"Simulation time steps"`: `values(args["network"]["mn_lookup"])`からコピーし、マルチネットワークIDでソート
  * `"Events"`: `args["raw_events"]`からコピー
  * `"Voltages"`: [`get_timestep_voltage_statistics!`](@ref get_timestep_voltage_statistics!)
  * `"Load served"`: [`get_timestep_load_served!`](@ref get_timestep_load_served!)
  * `"Generator profiles"`: [`get_timestep_generator_profiles!`](@ref get_timestep_generator_profiles!)
  * `"Storage SOC (%)"`: [`get_timestep_storage_soc!`](@ref get_timestep_storage_soc!)
  * `"Powerflow output"`: [`get_timestep_dispatch!`](@ref get_timestep_dispatch!)
  * `"Device action timeline"`: [`get_timestep_device_actions!`](@ref get_timestep_device_actions!)
  * `"Switch changes"`: [`get_timestep_switch_changes!`](@ref get_timestep_switch_changes!)
  * `"Small signal stability"`: [`get_timestep_stability!`](@ref get_timestep_stability!)
  * `"Fault currents"`: [`get_timestep_fault_currents!`](@ref get_timestep_fault_currents!)
  * `"Optimal dispatch metadata"`: [`get_timestep_dispatch_optimization_metadata!`](@ref get_timestep_dispatch_optimization_metadata!)
  * `"Optimal switching metadata"`: [`get_timestep_switch_optimization_metadata!`](@ref get_timestep_switch_optimization_metadata!)
