```
struct Output
```

The composite type for output.

  * `prob::FourierFlows.Problem`: the relevant problem for the output
  * `path::String`: the path for the output file
  * `fields::Dict{Symbol, Function}`: the fields to be saved; the relevant problem for this diagnostic
