```julia
struct TraceSummary{A<:BaytesCore.TemperingMethod, B<:Union{BaytesCore.DataTune, Vector{<:BaytesCore.DataTune}}, D<:BaytesCore.SampleDefault, S<:Baytes.SampleInfo}
```

Contains useful information for post-sampling analysis. Also allows to continue sampling with given sampler.

# Fields

  * `tempertune::BaytesCore.TemperingMethod`: Tuning container for temperature tempering
  * `datatune::Union{BaytesCore.DataTune, Vector{<:BaytesCore.DataTune}}`: Tuning container for data tempering
  * `default::BaytesCore.SampleDefault`: Default settings used for sample function
  * `info::Baytes.SampleInfo`: Information about trace used for postprocessing.
  * `progress::ProgressMeter.Progress`: Progress Log while sampling.
