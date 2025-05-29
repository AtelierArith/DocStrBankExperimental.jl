```julia
System(
    net_data::PowerSystems.PowerFlowDataNetwork;
    kwargs...
) -> PowerSystems.System

```

Constructs a System from PowerModelsData.

# Arguments

  * `pfd_data::Union{PowerFlowDataNetwork, Union{String, IO}}`: PowerModels data object or supported

load flow case (*.m, *.raw)

# Keyword arguments

  * `ext::Dict`: Contains user-defined parameters. Should only contain standard types.
  * `runchecks::Bool`: Run available checks on input fields and when add_component! is called. Throws InvalidValue if an error is found.
  * `time_series_in_memory::Bool=false`: Store time series data in memory instead of HDF5.
  * `config_path::String`: specify path to validation config file
  * `pm_data_corrections::Bool=true` : Run the PowerModels data corrections (aka :validate in PowerModels)
  * `import_all:Bool=false` : Import all fields from PTI files

# Examples

```julia
sys = System(
    pm_data, config_path = "ACTIVSg25k_validation.json",
    bus_name_formatter = x->string(x["name"]*"-"*string(x["index"])),
    load_name_formatter = x->strip(join(x["source_id"], "_"))
)
```
