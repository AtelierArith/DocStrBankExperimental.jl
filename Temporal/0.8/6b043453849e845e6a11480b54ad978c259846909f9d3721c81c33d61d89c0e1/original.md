```
collapse(x::TS, at::Function; fun::Function=last, args...)::TS
```

Compute the function `fun` over period boundaries defined by `at` (e.g. `eom`, `boq`, etc.) and returng a time series of the results.

Keyword arguments (`args...`) are passed to the function `fun`.
