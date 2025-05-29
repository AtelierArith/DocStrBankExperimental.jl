```julia
copy_time_series!(
    dst::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    src::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute};
    name_mapping,
    scaling_factor_multiplier_mapping
)

```

Efficiently add all time_series in one component to another by copying the underlying references.

# Arguments

  * `dst::TimeSeriesOwners`: Destination owner
  * `src::TimeSeriesOwners`: Source owner
  * `name_mapping::Dict = nothing`: Optionally map src names to different dst names. If provided and src has a `time_series` with a name not present in `name_mapping`, that `time_series` will not copied. If `name_mapping` is nothing then all `time_series` will be copied with src's names.
  * `scaling_factor_multiplier_mapping::Dict = nothing`: Optionally map src multipliers to different dst multipliers.  If provided and src has a `time_series` with a multiplier not present in `scaling_factor_multiplier_mapping`, that `time_series` will not copied. If `scaling_factor_multiplier_mapping` is nothing then all `time_series` will be copied with src's multipliers.
