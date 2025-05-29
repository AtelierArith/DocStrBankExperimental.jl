```julia
abstract type AbstractFactorization
```

Abstract type for a factorization   with ExtandableSparseMatrix. 

This type is meant to be a "type flexible" (with respect to the matrix element type) and lazily construcdet (can be constructed without knowing the matrix, and updated later) LU factorization or preconditioner. It wraps different concrete, type fixed factorizations which shall provide the usual `ldiv!` methods.

Any such preconditioner/factorization `MyFact` should have the following fields

```
  A::ExtendableSparseMatrix
  factorization
  phash::UInt64
```

and  provide methods

```
  MyFact(;kwargs...) 
  update!(precon::MyFact)
```

The idea is that, depending if the matrix pattern has changed,  different steps are needed to update the preconditioner.
