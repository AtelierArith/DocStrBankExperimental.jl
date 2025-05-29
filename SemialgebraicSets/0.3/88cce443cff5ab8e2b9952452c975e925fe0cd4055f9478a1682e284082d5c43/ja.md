```
struct ReorderedSchurMultiplicationMatricesSolver{T,RNGT<:Random.AbstractRNG} <:
    AbstractMultiplicationMatricesSolver
    ɛ::T
    rng::RNGT
end
```

可換行列の同時対角化 [CGT97] の手法を使用して。

[CGT97] Corless, R. M.; Gianni, P. M. & Trager, B. M. *A reordered Schur factorization method for zero-dimensional polynomial systems with multiple roots* Proceedings of the 1997 international symposium on Symbolic and algebraic computation, 1997, 133-140
