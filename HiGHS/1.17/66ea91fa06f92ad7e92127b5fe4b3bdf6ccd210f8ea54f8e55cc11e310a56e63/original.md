```
Highs_zeroAllClocks(highs)
```

Reset the clocks in a `highs` model.

Each `highs` model contains a single instance of clock that records how much time is spent in various parts of the algorithm. This clock is not reset on entry to [`Highs_run`](@ref), so repeated calls to [`Highs_run`](@ref) report the cumulative time spent in the algorithm. A side-effect is that this will trigger a time limit termination once the cumulative run time exceeds the time limit, rather than the run time of each individual call to [`Highs_run`](@ref).

As a work-around, call [`Highs_zeroAllClocks`](@ref) before each call to [`Highs_run`](@ref).

### Parameters

  * `highs`: A pointer to the Highs instance.

### Returns

A `kHighsStatus` constant indicating whether the call succeeded.
