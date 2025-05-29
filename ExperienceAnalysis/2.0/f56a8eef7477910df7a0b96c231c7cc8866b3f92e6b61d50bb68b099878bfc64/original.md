```
exposure(
    p::Anniversary,
    from::Date,
    to::Date,
    continued_exposure::Bool = false;
    study_start=typemin(from),
    study_end=typemax(from),
    left_partials::Bool=true,
    right_partials::Bool=true,
)::Vector{NamedTuple{(:from, :to, :policy_timestep),Tuple{Date,Date,Union{Int,Nothing}}}}
```

Calcualte the exposure periods and returns an array of named tuples with fields:

  * `from` (a `Date`) is the start date of the exposure interval
  * `to` (a `Date`) is the end of the exposure interval
  * `policy_step` will either be an `Int` if an Anniversary or AnniversaryCalendar basis is used, otherwise will be `nothing`

If `continued_exposure` is `true`, then the final `to` date will continue through the end of the final exposure period. This is useful if you want the decrement of interest is the cause of termination, because then you want a full exposure.

If `left_partials` or `right_partials` is set to false, then the exposure will not return partial exposure periods that overlap with the `study_start` and `study_end` respectively.

# Example

```julia-repl julia> using ExperienceAnalysis,Dates julia> exposure(     ExperienceAnalysis.Anniversary(Year(1)), # basis     Date(2020,5,10),                         # issue     Date(2022, 6, 10);                       # termination ) 3-element Vector{NamedTuple{(:from, :to, :policy*timestep), Tuple{Date, Date, Int64}}}:  (from = Date("2020-05-10"), to = Date("2021-05-09"), policy*timestep = 1)  (from = Date("2021-05-10"), to = Date("2022-05-09"), policy*timestep = 2)  (from = Date("2022-05-10"), to = Date("2022-06-10"), policy*timestep = 3)
