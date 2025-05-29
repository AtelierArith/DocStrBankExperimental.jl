```
mutable struct ReleaseStrategy
    release_this_gene_index::Union{Nothing, Int64}=nothing
    release_this_life_stage=nothing
    release_location_force::Union{Nothing, Bool}=nothing
    release_start_time::Union{Nothing,Int64}=nothing
    release_end_time::Union{Nothing,Int64}=nothing
    release_time_interval::Int64=1
    release_size_min_per_timestep::Union{Int64, Float64}=0.0
    release_size_max_per_timestep::Union{Int64,Float64}=9e9
    release_max_over_timehorizon::Union{Int64,Float64}=9e9

end
```

Data defining the operational constraints for each node.

# Arguments

  * `release_this_gene_index`: Gene index to be released. Generally defined by `get_homozygous_modified`.
  * `release_this_life_stage`: Lifestage to be released. Varies according to genetic technology.
  * `release_location_force`: Specify locations where releases are obligatory; only applicable when decision model is being run as an MINLP.
  * `release_start_time`: Timestep (day) that releases are permitted to start.
  * `release_end_time`: Timestep (day) that releases are required to end.
  * `release_time_interval`: Minimum timestep interval (in days) permitted for releases.
  * `release_size_min_per_timestep`: Minimum number of organisms that may be released on a single day.
  * `release_size_max_per_timestep`: Maximum number of organisms that may be released on a single day.
  * `release_max_over_timehorizon`: Maximum number of organisms that may be released over the problem horizon.
