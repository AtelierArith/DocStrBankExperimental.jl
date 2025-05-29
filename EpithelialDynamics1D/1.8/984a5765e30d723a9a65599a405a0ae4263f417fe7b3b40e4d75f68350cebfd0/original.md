```
get_knots(sol, num_knots = 500; indices = eachindex(sol), stat=maximum, parallel=false)
```

Computes knots for each time, covering the extremum of the cell positions across all  cell simulations. You can restrict the simultaions to consider using the `indices`. The knots are obtained by applying `stat`, a tuple of functions for the left and right sides, to the vector of extrema at each time. For example, if `stat=maximum` then, at each time,  the knots range between the smallest position observed and the maximum position  observed across each simulation at that time.
