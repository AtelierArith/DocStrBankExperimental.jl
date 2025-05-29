```
struct HomogeneousTPTProblem
```

A [`TPTProblem`](@ref) where the transition matrix is homogeneous, i.e. time-independent.

### Fields

  * `transition_matrix`: A [`TransitionMatrix`](@ref).
  * `source`: A vector of indices defining the TPT source, aka `A`.
  * `target`: A vector of indices defining the TPT target, aka `B`.

### Constructor

```
HomogeneousTPTProblem(P, source, target; avoid = Int64[])
```

Build a `HomogeneousTPTProblem` where each argument of the constructor maps to the corresponding field.

Optional Arguments 

  * `avoid`: Indices provided here will be appended to both `A` and `B` and will hence be avoided by transition path theory.
