```
struct NewtonTypeDiagonalization{T,RNGT} <: AbstractMultiplicationMatricesSolver
    max_iter::Int
    ε::T
    tol::T
    rng::RNGT
end
```

Simultaneous diagonalization of commuting matrices using the method of [KMY22, Theorem 5].

[KMY22] Khouja, Rima, Mourrain, Bernard, and Yakoubsohn, Jean-Claude. *Newton-type methods for simultaneous matrix diagonalization.* Calcolo 59.4 (2022): 38.
