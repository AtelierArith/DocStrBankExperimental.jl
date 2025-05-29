```
trappingtime(R[; lmin=2, theiler])
```

Calculate the trapping time of the recurrence matrix `R`, ruling out the lines shorter than `lmin` (2 by default) and all the points inside the Theiler window (see [`rqa`](@ref) for the default values and usage of the keyword argument `theiler`).

The trapping time is the average of the vertical line structures and thus equal to [`vl_average`](@ref).
