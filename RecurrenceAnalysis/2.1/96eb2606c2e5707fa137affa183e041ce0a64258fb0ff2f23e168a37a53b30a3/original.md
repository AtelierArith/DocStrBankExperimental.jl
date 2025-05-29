```
RecurrenceMatrix(x, rthres; metric = Euclidean(), parallel::Bool)
```

Create a recurrence matrix from timeseries or trajectory `x` and with recurrence threshold `rthres`. `x` is either a [`StateSpaceSet`](@ref) for multivariate data or an `AbstractVector{<:Real}` for timeseries.

The variable `rthres` defines how recurrences are estimated. It can be any subtype of [`AbstractRecurrenceType`](@ref), and different types can specify recurrences differently. Alternatively, `rthres` can be a real number, which then becomes an instance of [`RecurrenceThreshold`](@ref).

The keyword `metric`, if given, must be any subtype of `Metric` from [Distances.jl](https://github.com/JuliaStats/Distances.jl) and defines the metric used to calculate distances for recurrences. By default the Euclidean metric is used, typical alternatives are `Chebyshev(), Cityblock()`.

The keyword `parallel` decides if the comptutation should be done in parallel using threads. Defaults to `length(x) > 500 && Threads.nthreads() > 1`.

## Description

A (cross-)recurrence matrix is a way to quantify *recurrences* that occur in a trajectory. A recurrence happens when a trajectory visits the same neighborhood on the state space that it was at some previous time.

The recurrence matrix is a numeric representation of a recurrence plot, described in detail in [^Marwan2007] and [^Marwan2015]. It represents a a sparse square matrix of Boolean values that quantifies recurrences in the trajectory, i.e., points where the trajectory returns close to itself. Given trajectories `x, y`, and asumming `ε isa Real`, the matrix is defined as:

```julia
R[i,j] = metric(x[i], y[i]) ≤ ε ? true : false
```

with the `metric` being the distance function. The difference between a `RecurrenceMatrix` and a [`CrossRecurrenceMatrix`](@ref) is that in the first case `x === y`.

Objects of type `<:AbstractRecurrenceMatrix` are displayed as a [`recurrenceplot`](@ref).

See also: [`CrossRecurrenceMatrix`](@ref), [`JointRecurrenceMatrix`](@ref) and use [`recurrenceplot`](@ref) to turn the result of these functions into a plottable format.

[^Marwan2007]: N. Marwan *et al.*, "Recurrence plots for the analysis of complex systems", [Phys. Reports 438*(5-6), 237-329 (2007)](https://doi.org/10.1016/j.physrep.2006.11.001)

[^Marwan2015]: N. Marwan & C.L. Webber, *Recurrence Quantification Analysis. Theory and Best Practices* [Springer (2015)](https://link.springer.com/book/10.1007/978-3-319-07155-8)
