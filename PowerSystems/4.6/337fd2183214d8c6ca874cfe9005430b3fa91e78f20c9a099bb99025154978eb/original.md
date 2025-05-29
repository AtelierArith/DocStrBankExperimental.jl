```julia
PowerSystemTableData(
    directory::AbstractString,
    base_power::Float64,
    user_descriptor_file::AbstractString;
    descriptor_file,
    generator_mapping_file,
    timeseries_metadata_file
) -> PowerSystems.PowerSystemTableData

```

Reads in all the data stored in csv files The general format for data is     folder:         gen.csv         branch.csv         bus.csv         ..         load.csv

# Arguments

  * `directory::AbstractString`: directory containing CSV files
  * `base_power::Float64`: base power for System
  * `user_descriptor_file::AbstractString`: customized input descriptor file
  * `descriptor_file=POWER_SYSTEM_DESCRIPTOR_FILE`: PowerSystems descriptor file
  * `generator_mapping_file=GENERATOR_MAPPING_FILE`: generator mapping configuration file
