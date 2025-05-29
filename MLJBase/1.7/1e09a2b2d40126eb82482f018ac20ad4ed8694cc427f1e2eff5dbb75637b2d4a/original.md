```
report(signature; supplement=true)
```

**Private method.**

Generate a report for the learning network associated with `signature`, including the supplementary report.

Suppress calling of the report nodes of `signature`, and excluded their contribution to the output, by specifying `supplement=false`.

See also [`MLJBase.report_supplement`](@ref).

See also [`MLJBase.Signature`](@ref).
