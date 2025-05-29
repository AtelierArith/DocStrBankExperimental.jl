```
hermitian_local_genera(E::NumField, p::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, rank::Int,
                       det_val::Int, min_scale::Int, max_scale::Int)
                                                  -> Vector{HermLocalGenus}
```

Return all local genus symbols for hermitian lattices over the algebra `E`, with base field $K$, at the prime ideal`p` of $\mathcal O_K$. Each of them has rank equal to `rank`, scale $\mathfrak P$-valuations bounded between `min_scale` and `max_scale` and determinant `p`-valuations equal to `det_val`, where $\mathfrak P$ is a prime ideal of $\mathcal O_E$ lying above `p`.
