```julia
abstract type AbstractFactorization{Tv, Ti}
```

Abstract type for a factorization   with ExtandableSparseMatrix. 

Any such preconditioner should have the following fields

```
  A::ExtendableSparseMatrix
  fact
  phash::UInt64
```

and  provide a method

```
  update!(precon)
```

The idea is that, depending if the matrix pattern has changed,    different steps are needed to update the preconditioner.

Moreover, they have the ExtendableSparseMatrix `A` as a field and an `update!` method, ensuring    consistency after construction.
