```
DeviceModel(
    ::Type{D},
    ::Type{B},
    feedforwards::Vector{<:AbstractAffectFeedforward}
    use_slacks::Bool,
    duals::Vector{DataType},
    services::Vector{ServiceModel}
    attributes::Dict{String, Any}
)
```

Establishes the model for a particular device specified by type. Uses the keyword argument feedforward to enable passing values between operation model at simulation time

# Arguments

  * `::Type{D} where D<:PSY.Device`: Power System Device Type
  * `::Type{B} where B<:AbstractDeviceFormulation`: Abstract Device Formulation
  * `feedforward::Array{<:AbstractAffectFeedforward} = Vector{AbstractAffectFeedforward}()` : use to pass parameters between models
  * `use_slacks::Bool = false` : Add slacks to the device model. Implementation is model dependent and not all models feature slacks
  * `duals::Vector{DataType} = Vector{DataType}()`: use to pass constraint type to calculate the duals. The DataType needs to be a valid ConstraintType
  * `time_series_names::Dict{Type{<:TimeSeriesParameter}, String} = get_default_time_series_names(D, B)` : use to specify time series names associated to the device`
  * `attributes::Dict{String, Any} = get_default_attributes(D, B)` : use to specify attributes to the device

# Example

```julia
thermal_gens = DeviceModel(ThermalStandard, ThermalBasicUnitCommitment)
```
