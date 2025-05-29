```
AbstractRecurrenceType
```

Supertype of all recurrence specification types. Instances of subtypes are given to [`RecurrenceMatrix`](@ref) and similar constructors to specify recurrences. Use [`recurrence_threshold`](@ref) to extract the numeric distance threshold.

Possible subtypes are:

  * `RecurrenceThreshold(ε::Real)`: Recurrences are defined as any point with distance `≤ ε` from the referrence point.
  * `RecurrenceThresholdScaled(ratio::Real, scale::Function)`: Here `scale` is a function of the distance matrix `dm` (see [`distancematrix`](@ref)) that is used to scale the value of the recurrence threshold `ε` so that `ε = ratio*scale(dm)`. After the new `ε` is obtained, the method works just like the `RecurrenceThreshold`. Specialized versions are employed if `scale` is `mean` or `maximum`.
  * `GlobalRecurrenceRate(q::Real)`: Here the number of total recurrence rate over the whole matrix is specified to be a quantile `q ∈ (0,1)` of the [`distancematrix`](@ref). In practice this yields (approximately) a ratio `q` of recurrences out of the total `Nx * Ny` for input trajectories `x, y`.
  * `LocalRecurrenceRate(r::Real)`: The recurrence threhsold here is point-dependent. It is defined so that each point of `x` has a fixed number of `k = r*N` neighbors, with ratio `r` out of the total possible `N`. Equivalently, this means that each column of the recurrence matrix will have exactly `k` true entries. Notice that `LocalRecurrenceRate` does not guarantee that the resulting recurrence matrix will be symmetric.
