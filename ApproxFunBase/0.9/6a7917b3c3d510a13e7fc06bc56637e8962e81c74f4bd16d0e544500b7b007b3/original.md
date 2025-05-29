```
SymmetricEigensystem(L::Operator, B::Operator, QuotientSpaceType::Type = QuotientSpace)
```

Represent the eigensystem `L v = λ v` subject to `B v = 0`, where `L` is self-adjoint with respect to the standard `L2` inner product given the boundary conditions `B`.

!!! note
    No tests are performed to assert that the operator `L` is self-adjoint, and it's the user's responsibility to ensure that the operators are compliant.


The optional argument `QuotientSpaceType` specifies the type of space to be used to denote the quotient space in the basis recombination process. In most cases, the default choice of `QuotientSpace` is a good one. In specific instances where `B` is rank-deficient (e.g. it contains a column of zeros, which typically happens if one of the basis elements already satiafies the boundary conditions), one may need to choose this to be a `PathologicalQuotientSpace`.

!!! note
    No checks on the rank of `B` are carried out, and it's up to the user to specify the correct type.

