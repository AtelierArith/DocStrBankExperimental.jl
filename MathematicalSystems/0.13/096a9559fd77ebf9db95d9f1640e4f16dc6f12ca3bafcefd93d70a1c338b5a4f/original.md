```
successor(system::AbstractDiscreteSystem, x::AbstractVector, u::AbstractVector;
          [check_constraints]=true)
```

Return the successor state of an `AbstractDiscreteSystem`.

### Input

  * `system`            – `AbstractDiscreteSystem`
  * `x`                 – state (it should be any vector type)
  * `u`                 – input (it should be any vector type) or noise, if `system`                        is not controlled
  * `check_constraints` – (optional, default: `true`) check if the state belongs to                        the state set

### Output

The result of applying the system to state `x` and input `u`.

### Notes

If the system is not controlled but noisy, the input `u` is interpreted as noise.
