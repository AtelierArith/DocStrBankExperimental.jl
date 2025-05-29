```
discretize_solution(solution::SciMLBase.AbstractTimeseriesSolution[, time_ref::SciMLBase.AbstractTimeseriesSolution]; measured=nothing, all_observed=false)
```

`discretize_solution` takes a solution and an optional time reference and converts it into a dataframe. This dataframe will contain either:

  * The variables (unknowns or observeds) named in `measured`, if provided.
  * The variables marked as `measured` if `all_observed` is `false` and `measured` is `nothing`.
  * All variables in the system if `all_observed` is `true` and `measured` is `nothing`.

The dataframe will contain a column called `timestamp` for each of the discretization times and a column for each observed value.

If no time reference is provided then the timebase used to discretize `solution` will be used instead. 
