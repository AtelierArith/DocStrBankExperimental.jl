```
successor(system::ConstrainedDiscreteIdentitySystem, x::AbstractVector;
          [check_constraints]=true)
```

Return the successor state of a `ConstrainedDiscreteIdentitySystem`.

### Input

  * `system`            – `ConstrainedDiscreteIdentitySystem`
  * `x`                 – state (it should be any vector type)
  * `check_constraints` – (optional, default: `true`) check if the state belongs to                        the state set

### Output

The same state `x`.
