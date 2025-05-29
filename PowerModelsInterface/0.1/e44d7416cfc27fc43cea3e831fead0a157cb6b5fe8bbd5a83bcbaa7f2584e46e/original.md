Creates a PowerModels data dictionary from a PowerSystems `System`. To populate time series data in the resulting dataset, pass `start_time` kwarg along with either `period` for a single time period, or `time_periods` to create a multi-network dataset with multiple time periods

# Arguments

  * `sys::System`: PowerSystems System

# Key word arguments

  * `name::String`: system name
  * `start_time::DateTime`: `System` forecast initial time
  * `time_periods::UnitRange{Int}=1:PSY.get_forecast_horizon(sys)`: indices for selecting forecast periods. Valid extent is `1:horizon`
  * `period::Int=1`: index for selecting forecast period. Valid options
