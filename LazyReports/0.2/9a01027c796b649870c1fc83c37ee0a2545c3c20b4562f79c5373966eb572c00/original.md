```
lazyreport!(rpt::LazyReport, contents...)
```

Add more content to report `rpt`. See [`lazyreport`](@ref) for an example.

# Implementation

Do not specialize `lazyreport!(rpt::LazyReport, obj::MyType)` directly, specialize the lower-level function [`LazyReports.pushcontent!`](@ref) instead.
