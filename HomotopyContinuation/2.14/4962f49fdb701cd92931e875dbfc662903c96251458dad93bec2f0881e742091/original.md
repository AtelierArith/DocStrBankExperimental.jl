```
OverdeterminedTracker(tracker::AbstractPathTracker, F::RandomizedSystem)
```

Wraps the given [`AbstractPathTracker`](@ref) `tracker` to apply [`excess_solution_check`](@ref) for the given randomized system `F` on each path result.
