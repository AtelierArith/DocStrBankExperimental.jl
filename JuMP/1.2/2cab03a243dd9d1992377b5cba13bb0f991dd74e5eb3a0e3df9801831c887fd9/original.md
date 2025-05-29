```
AbstractJuMPScalar <: MutableArithmetics.AbstractMutable
```

Abstract base type for all scalar types

The subtyping of `AbstractMutable` will allow calls of some `Base` functions to be redirected to a method in MA that handles type promotion more carefully (e.g. the promotion in sparse matrix products in SparseArrays usually does not work for JuMP types) and exploits the mutability of `AffExpr` and `QuadExpr`.
