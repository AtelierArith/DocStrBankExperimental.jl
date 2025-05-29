```julia
struct ProposalTune{F<:Real, U<:BaytesCore.UpdateBool, T<:BaytesCore.DataTune}
```

Proposal function tuning struct.

Contains information for proposal step of algorithm that is on a higher level and shared among different sampler, like data indexing, and is not stored in algorithm struct.

# Fields

  * `temperature::Real`: Temperature for log objective tempering.
  * `update::BaytesCore.UpdateBool`: Quasi-Boolean if Algorithm has to be updated with new parameter before proposal step.
  * `datatune::BaytesCore.DataTune`: Information at which iteration data indexing is at the moment.
