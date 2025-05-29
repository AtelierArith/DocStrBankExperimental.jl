```
vector_field(system::AbstractContinuousSystem,
          x::AbstractVector, u::AbstractVector, w::AbstractVector; [check_constraints]=true)
```

Return the vector field state of an `AbstractContinuousSystem`.

### Input

  * `system`            – `AbstractContinuousSystem`
  * `x`                 – state (it should be any vector type)
  * `u`                 – input (it should be any vector type)
  * `w`                 – noise (it should be any vector type)
  * `check_constraints` – (optional, default: `true`) check if the state belongs to                        the state set

### Output

The vector field of the system at state `x` and applying input `u` and noise `w`.
