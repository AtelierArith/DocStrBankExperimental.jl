```
JointRecurrenceMatrix(x, y, rthres; kwargs...)
```

Create a joint recurrence matrix from trajectories `x` and `y`. See [`RecurrenceMatrix`](@ref) for possible values for `rthres` and `kwargs`.

The joint recurrence matrix considers the recurrences of the trajectories of `x` and `y` separately, and looks for points where both recur simultaneously. It is calculated by the element-wise multiplication of the recurrence matrices of `x` and `y`. If `x` and `y` are of different length, the recurrences are only calculated until the length of the shortest one.

See [`RecurrenceMatrix`](@ref) for details, references and keywords.
