```
sorteddistances(x; kwargs...)
```

Return a tuple with the sorted distances between points of the embedded time series `x`, and the recurrence rates under those values.

The keyword arguments are the same that should be passed to the functions `recurrencematrix` and `recurrencerate` to obtain those results. I.e., if `d,r = sorteddistances(x; kwargs...)`, and `rmat = recurrencematrix(x, d[i]; kwargs...)`, then `recurrencerate(rmat; kwargs...) == r[i]`.
