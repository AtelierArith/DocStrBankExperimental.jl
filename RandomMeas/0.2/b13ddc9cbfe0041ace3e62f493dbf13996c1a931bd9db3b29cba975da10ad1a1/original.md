```
get_expect_shadow(O::MPO, shadows::AbstractArray{<:AbstractShadow}; compute_sem::Bool = false)
```

Compute the average expectation value of an MPO operator `O` using an array of shadow objects.

# Arguments

  * `O::MPO`: The MPO operator whose expectation value is to be computed.
  * `shadows::AbstractArray{<:AbstractShadow}`: An array of shadow objects (of any shape) over which the expectation values are computed.
  * `compute_sem::Bool` (optional): If `true`, also compute the standard error of the mean (SEM). Default is `false`.

# Returns

  * If `compute_sem` is `false`, returns the average expectation value.
  * If `compute_sem` is `true`, returns a tuple `(mean, sem)`, where `mean` is the average expectation value and `sem` is the standard error.

# Example

```julia
mean_val = get_expect_shadow(O, shadows)
mean_val, sem_val = get_expect_shadow(O, shadows; compute_sem=true)
```
