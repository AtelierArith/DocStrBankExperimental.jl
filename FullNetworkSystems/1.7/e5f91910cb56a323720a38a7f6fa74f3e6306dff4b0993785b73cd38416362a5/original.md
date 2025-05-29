```julia
mutable struct SystemDA <: FullNetworkSystems.System
```

Subtype of a `System` for modelling the day-ahead market.

Fields:

  * `gens_per_bus::Dictionaries.Dictionary{InlineStrings.String15, Vector{Int64}}`: `Dictionary` where the keys are bus names and the values are generator ids at that bus
  * `incs_per_bus::Dictionaries.Dictionary{InlineStrings.String15, Vector{InlineStrings.String31}}`: `Dictionary` where the keys are bus names and the values are increment bid ids at that bus
  * `decs_per_bus::Dictionaries.Dictionary{InlineStrings.String15, Vector{InlineStrings.String31}}`: `Dictionary` where the keys are bus names and the values are decrement bid ids at that bus
  * `psls_per_bus::Dictionaries.Dictionary{InlineStrings.String15, Vector{InlineStrings.String31}}`: `Dictionary` where the keys are bus names and the values are price sensitive load bid ids at that bus

  * `loads_per_bus::Dictionaries.Dictionary{InlineStrings.String15, Vector{InlineStrings.String31}}`: `Dictionary` where the keys are bus names and the values are load ids at that bus
  * `zones::Dictionaries.Dictionary{Int64, FullNetworkSystems.Zone}`: Zones in the `System`, which will also include a `Zone` entry for the market wide zone
  * `buses::Dictionaries.Dictionary{InlineStrings.String15, FullNetworkSystems.Bus}`: Buses in the `System` indexed by bus name
  * `generators::Dictionaries.Dictionary{Int64, FullNetworkSystems.Generator}`: Generators in the `System` indexed by unit code
  * `branches::Dictionaries.Dictionary{InlineStrings.String31, FullNetworkSystems.Branch}`: Branches in the `System` indexed by branch name
  * `lodfs::Dictionaries.Dictionary{String, AxisKeys.KeyedArray{Float64, 2}}`: The line outage distribution factor matrix of the system for a set of contingencies given by the keys of the `Dictionary`. Each entry is a `KeyedArray` with axis keys `branch names x branch on outage`

  * `ptdf::Union{Missing, AxisKeys.KeyedArray{Float64, 2}}`: Power transfer distribution factor of the system.  `KeyedArray` where the axis keys are `branch names x bus names`

  * `generator_time_series::FullNetworkSystems.GeneratorTimeSeries`: Generator related time series data
  * `generator_status::FullNetworkSystems.GeneratorStatusDA`: Generator status time series needed for the day-ahead formulation
  * `loads::AxisKeys.KeyedArray{Float64, 2}`: Load time series data. `KeyedArray` where the axis keys are `load ids x datetimes`
  * `increments::AxisKeys.KeyedArray{Vector{Tuple{Float64, Float64}}, 2}`: Increment bids time series data. `KeyedArray` where the axis keys are `bid ids x datetimes`
  * `decrements::AxisKeys.KeyedArray{Vector{Tuple{Float64, Float64}}, 2}`: Decrement bids time series data. `KeyedArray` where the axis keys are `bid ids x datetimes`
  * `price_sensitive_loads::AxisKeys.KeyedArray{Vector{Tuple{Float64, Float64}}, 2}`: Price sensitive load bids time series data. `KeyedArray` where the axis keys are `bid ids x datetimes`
