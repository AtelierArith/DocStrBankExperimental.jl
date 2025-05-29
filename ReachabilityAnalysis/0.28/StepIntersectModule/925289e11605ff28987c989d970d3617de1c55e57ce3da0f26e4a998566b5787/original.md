```
StepIntersect{DM<:AbstractApproximationModel} <: AbstractApproximationModel
```

Approximation model that composes (intersecting) one step Forward of a given model with one step backward of the same model.

### Fields

  * `model`  – approximation model
  * `setops` – set operations method

### Notes

Let $x' = Ax$ with $x(0) ∈ X₀$. This methods consists of:

  * Compute the discretized system with step-size $δ$ obtaining $Ω0$ and the given approximation model `method`.
  * Compute the (lazy) linear map $ΦX₀$. This set consists of the (exact) reachable states at the time point $δ$.
  * Apply the approximation model `method` with initial condition $ΦX₀$ one step backward in time, with the state transition matrix $-A$, call this reach-set $Ω₀₊$
  * Intersect $Ω₀₋$ and $Ω₀₊$ and return such set. The intersection is done either lazily or concretely depending on the specified `setops` field.
