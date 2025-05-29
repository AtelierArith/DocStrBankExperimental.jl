```
successor(system::AbstractDiscreteSystem,
          x::AbstractVector, u::AbstractVector, w::AbstractVector; [check_constraints]=true)
```

Return the successor state of an `AbstractDiscreteSystem`.

### Input

  * `system`            – `AbstractDiscreteSystem`
  * `x`                 – state (it should be any vector type)
  * `u`                 – input (it should be any vector type)
  * `w`                 – noise (it should be any vector type)
  * `check_constraints` – (optional, default: `true`) check if the state belongs to                        the state set

### Output

The result of applying the system to state `x`, input `u` and noise `w`.
