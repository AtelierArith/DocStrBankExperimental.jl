```
bandmatrices_eigen(S::Union{SymmetricEigensystem, SkewSymmetricEigensystem}, n::Integer)
```

Recast the symmetric/skew-symmetric eigenvalue problem `L v = λ v` subject to `B v = 0` to the generalized eigenvalue problem `SA v = λ SB v`, where `SA` and `SB` are banded operators, and return the `n × n` matrix representations of `SA` and `SB`. If `S isa SymmetricEigensystem`, the returned matrices will be `Symmetric`.

!!! note
    No tests are performed to assert that the system is symmetric/skew-symmetric, and it's the user's responsibility to ensure that the operators are compliant.

