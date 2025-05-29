```
StepsizeState{P,T} <: AbstractManoptSolverState
```

A state to store a point and a descent direction used within a linesearch, if these are different from the iterate and search direction of the main solver.

# Fields

  * `p::P`: a point on a manifold
  * `X::T`: a tangent vector at `p`.

# Constructor

```
StepsizeState(p,X)
```

# See also

[`interior_point_Newton`](@ref)
