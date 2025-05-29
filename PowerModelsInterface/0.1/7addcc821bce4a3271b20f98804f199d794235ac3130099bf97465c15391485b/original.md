Applies a single time period of time series data from a PowerSystems `System` to a PowerModels data dictionary.

# Arguments

  * `pm_data::Dict{String, Any}`: PowerModels dictionary data
  * `sys::System`: PowerSystems System
  * `start_time::Dates.DateTime`: initial time of `Forecast`
  * `time_period::Int`: time period index of `Forecast`
