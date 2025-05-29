```julia
struct VariableDFG <: DistributedFactorGraphs.AbstractDFGVariable
```

The Variable information packed in a way that accomdates multi-lang using json.

Notes:

  * timestamp is a `ZonedDateTime` in UTC.
  * nstime can be used as mission time, with the convention that the timestamp millis coincide with the mission start nstime

      * e.g. timestamp is `2020-01-01 06:30:01.250 UTC` and first nstime is `250_000_000`.
