```
optimize_presentation_schedule(
    individuals :: AbstractVector{IT},
    dates :: AbstractVector{DT},
    [presentations_modify, journals_modify, cannot_attend]...; 
    kwargs...
    ) where {IT <: Union{Int, String}, DT <: Union{Date, Int}}
```

Given iterables of `individuals` and `dates`, plan a meeting schedule which allocates research presentations and journal club presentations to each presentation date across individuals, aiming to space out the presentations of each individual evenly.

Returns a an optimized schedule, wrapping a JuMP model, which displays as a table.

## Optional arguments

  * `presentations_modify :: Dict{IT, Int}`: each individual is scheduled to present `default_presentations` research presentations (see Keyword arguments). To override this, add a `key=>value` pair to `presentation_modify` for the individual. E.g., `presentations_modify = Dict("Individual A" => 1)`.
  * `journals_modify :: Dict{IT, Int}`: same as `presentations_modify` but to override the number of journal club presentations for specific individuals.
  * `cannot attend :: Dict{IT, <:AbstractVector{DT}}`: a list of dates, overlapping with those in `dates`, one which a specific individual is unable to present. E.g., `cannot_attend = Dict("Individual A" => Date("21/01/2024"))`.

Optional arguments default to empty containers if unspecified.

## Keyword arguments

  * `default_presentations :: Int` (default, `2`): default number of research presentations per individual; overridable via the optional argument `presentations_modify`.
  * `default_journals :: Int` (default, `1`): default number of journal club presentations per individual; overridable via the optional argument `journals_modify`.
  * `min_total :: Int` (default, `2`): minimum number of total presentations (research *and* journal club) per meeting date.
  * `max_total :: Int` (default, `4`): maximum number of total presentations (research *and* journal club) per meeting date.
  * `min_presentations :: Int` (default, `1`): minimum number of research presentations per meeting date.
  * `max_presentations :: Int` (default, `3`): maximum number of research presentations per meeting date.
  * `min_journals :: Int` (default, `0`): minimum number of journal club presentations per meeting date.
  * `max_journals :: Int` (default, `1`): maximum number of journal club presentations per meeting date.
  * `time_limit :: Real` (default, `60`): time limit imposed on optimizer in seconds; note that a provably optimal schedule usually is impractically slow to compute.
