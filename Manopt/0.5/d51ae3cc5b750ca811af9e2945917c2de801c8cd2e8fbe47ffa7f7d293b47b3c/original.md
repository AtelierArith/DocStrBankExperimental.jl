```
InplaceEvaluation <: AbstractEvaluationType
```

A parameter for a [`AbstractManoptProblem`](@ref) indicating that the problem uses functions that do not allocate memory but work on their input, in place.
