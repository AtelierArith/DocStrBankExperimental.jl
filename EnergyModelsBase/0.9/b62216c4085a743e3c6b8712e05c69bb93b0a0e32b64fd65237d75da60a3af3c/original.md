```
process_emissions(data::EmissionsData)
process_emissions(data::EmissionsData{T}, p::ResourceEmit)
process_emissions(data::EmissionsData{T}, p:ResourceEmit, t)
```

Returns the [`ResourceEmit`](@ref)s that have process emissions of the [`EmissionsData`](@ref) `data`.

When the [`ResourceEmit`](@ref) `p` is specified, it returns the process emissions as `TimeProfile` (`FixedProfile`, if the emissions are provided as `Float64` and `FixedProfile(0)` if no values are provided.)

When the [`ResourceEmit`](@ref) `p` and the operational period `t` are specified, it returns the value (or 0, if there are no process emissions for the specifed `ResourceEmit` `p`).
