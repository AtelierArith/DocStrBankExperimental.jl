```
meanrecurrencetime(R[; lmin=2, theiler])
```

Calculate the mean recurrence time of the recurrence matrix `R`, ruling out the lines shorter than `lmin` (2 by default) and all the points inside the Theiler window (see [`rqa`](@ref) for the default values and usage of the keyword argument `theiler`).

Equivalent to [`rt_average`](@ref).
