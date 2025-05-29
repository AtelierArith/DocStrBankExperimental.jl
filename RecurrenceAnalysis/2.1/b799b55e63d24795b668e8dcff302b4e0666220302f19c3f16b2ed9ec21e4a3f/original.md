```
dl_max(R[; lmin=2, theiler])
```

Calculate the longest diagonal line contained in the recurrence matrix `R`, ruling out the lines shorter than `lmin` (2 by default) and all the points inside the Theiler window (see [`rqa`](@ref) for the default values and usage of the keyword argument `theiler`).
