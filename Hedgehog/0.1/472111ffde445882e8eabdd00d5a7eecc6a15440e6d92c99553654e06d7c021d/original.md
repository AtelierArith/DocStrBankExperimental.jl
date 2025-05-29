```
solve(calib::CalibrationProblem, calib_algo::RootFinderAlgo; kwargs...)
```

Solves for a single implied parameter (e.g., implied volatility) using root-finding.

Returns the solution object with `.u` as the calibrated value.
