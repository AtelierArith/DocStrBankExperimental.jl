```
struct NewtonTypeDiagonalization{T,RNGT} <: AbstractMultiplicationMatricesSolver
    max_iter::Int
    ε::T
    tol::T
    rng::RNGT
end
```

可換行列の同時対角化を[KMY22, Theorem 5]の方法を用いて行います。

[KMY22] Khouja, Rima, Mourrain, Bernard, and Yakoubsohn, Jean-Claude. *Newton-type methods for simultaneous matrix diagonalization.* Calcolo 59.4 (2022): 38.
