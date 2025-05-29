```
vector_field(system::AbstractContinuousSystem, x::AbstractVector, u::AbstractVector;
          [check_constraints]=true)
```

Return the vector field state of an `AbstractContinuousSystem`.

### Input

  * `system`            – `AbstractContinuousSystem`
  * `x`                 – state (it should be any vector type)
  * `u`                 – input (it should be any vector type) or noise, if `system`                        is not controlled
  * `check_constraints` – (optional, default: `true`) check if the state belongs to                        the state set

### Output

The vector field of the system at state `x` and applying input `u`.

### Notes

If the system is not controlled but noisy, the input `u` is interpreted as noise.
