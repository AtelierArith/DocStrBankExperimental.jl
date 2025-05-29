```
Specification(problem::Problem)
```

Constructs a `Specification` of the appropriate concrete type based on the information contained in the PDDL `Problem`. If no metric formula is specified, a [`MinStepsGoal`](@ref) specification is returned. Otherwise, one of [`MinMetricGoal`](@ref) or [`MaxMetricGoal`](@ref) are returned.
