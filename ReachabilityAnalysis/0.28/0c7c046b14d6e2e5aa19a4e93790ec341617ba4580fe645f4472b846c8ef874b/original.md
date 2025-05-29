```
A20{N} <: AbstractContinuousPost
```

Implementation of the reachability method for large linear systems with uncertain inputs in the Krylov subspace from [Althoff20](@citet).

### Fields

  * `δ`          – step-size of the discretization
  * `max_order`  – (optional, default: `5`) maximum zonotope order

### References

See [Althoff20](@citet) and references therein.
