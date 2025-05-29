```
prefilter(d::AbstractIdData, responsetype::FilterType)
```

Filter both input and output of the identification data using zero-phase filtering (`filtfilt`). Since both input and output is filtered, linear identification will not be affected in any other way than to focus the fit on the selected frequency range, i.e. the range that has high gain in the provided filter. Note, if the system that generated `d` is nonlinear, identification might be severely impacted by this transformation. Verify linearity with, e.g., [`coherenceplot`](@ref).
