```
QuasiNewtonPreconditioner{E<:AbstractEvaluationType, F}
```

Add a preconditioning

# Fields

  * `preconditioner::F`: the preconditioner function

# Constructors

```
QuasiNewtonPreconditioner(
    preconditioner;
    evaluation::AbstractEvaluationType=AllocatingEvaluation()
)
```

Add preconditioning to a gradient problem.

# Input

  * `preconditioner`:   preconditioner function, either as a `(M, p, X) -> Y` allocating or `(M, Y, p, X) -> Y` mutating function

# Keyword arguments

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: specify whether the functions that return an array, for example a point or a tangent vector, work by allocating its result ([`AllocatingEvaluation`](@ref)) or whether they modify their input argument to return the result therein ([`InplaceEvaluation`](@ref)). Since usually the first argument is the manifold, the modified argument is the second.
