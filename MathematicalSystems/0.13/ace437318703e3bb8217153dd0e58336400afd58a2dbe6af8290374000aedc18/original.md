```
vector_field(system::ConstrainedContinuousIdentitySystem, x::AbstractVector;
          [check_constraints]=true)
```

Return the vector field state of a `ConstrainedContinuousIdentitySystem`.

### Input

  * `system`            – `ConstrainedContinuousIdentitySystem`
  * `x`                 – state (it should be any vector type)
  * `check_constraints` – (optional, default: `true`) check if the state belongs to                        the state set

### Output

A zeros vector of dimension `statedim`.
