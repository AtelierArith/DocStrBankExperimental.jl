```
phiv(t,A,b,k;correct,kwargs) -> [phi_0(tA)b phi_1(tA)b ... phi_k(tA)b][, errest]
```

Compute the matrix-phi-vector products using Krylov. `k` >= 1.

The phi functions are defined as

$$
\varphi_0(z) = \exp(z),\quad \varphi_{k+1}(z) = \frac{\varphi_k(z) - 1}{z}
$$

A Krylov subspace is constructed using `arnoldi` and `phiv_dense` is called on the Hessenberg matrix. If `correct=true`, then phi*0 through phi*k-1 are updated using the last Arnoldi vector v_m+1 [^1]. If `errest=true` then an additional error estimate for the second-to-last phi is also returned. For the additional keyword arguments, consult `arnoldi`.

phiv(t,Ks,k;correct,kwargs) -> [phi*0(tA)b phi*1(tA)b ... phi_k(tA)b][, errest]

Compute the matrix-phi-vector products using a pre-constructed Krylov subspace.

[^1]: Niesen, J., & Wright, W. (2009). A Krylov subspace algorithm for evaluating the φ-functions in exponential integrators. arXiv preprint arXiv:0907.4631. Formula (10).
