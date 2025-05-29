```
struct DCLine <: Modification
    
DCLine(;file)
```

This [`Modification`](@ref) takes in a file representing the dc lines to add to the model.  See [`summarize_table(::Val{:dc_line})`](@ref) for info on the table.

This creates a single variable for each dc line (at each point in time), and adds it to `pbal_bus` of the `t_bus_idx`, and subtracts it from the `f_bus_idx`.  Represents a lossless transfer of power, ignoring voltage angle requirements.

# Interfaces Implemented

  * [`modify_raw_data!(mod::DCLine, config, data)`](@ref) - loads `mod.file => data[:dc_line]`
  * [`modify_model!(mod::DCLine, config, data, model)`](@ref) - Add dc lines to the model from `data[:dc_lines]`, creating `pflow_dc` variables, and adding/subtracting to the corresponding `pflow_bus` variables.
