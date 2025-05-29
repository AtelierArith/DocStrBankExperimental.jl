```
info::MethodMatchInfo <: CallInfo
```

Captures the result of a `:jl_matching_methods` lookup for the given call (`info.results`). This info may then be used by the optimizer to inline the matches, without having to re-consult the method table. This info is illegal on any statement that is not a call to a generic function.
