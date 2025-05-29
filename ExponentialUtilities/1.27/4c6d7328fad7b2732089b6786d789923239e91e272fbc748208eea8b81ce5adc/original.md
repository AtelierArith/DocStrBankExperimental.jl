```
phi(A,k[;cache]) -> [phi_0(A),phi_1(A),...,phi_k(A)]
```

Compute the matrix phi functions for all orders up to k. `k` >= 1.

The phi functions are defined as

$$
\varphi_0(z) = \exp(z),\quad \varphi_{k+1}(z) = \frac{\varphi_k(z) - 1}{z}
$$

Calls `phiv_dense` on each of the basis vectors to obtain the answer. If A is `Diagonal`, instead calls the scalar `phi` on each diagonal element and the return values are also `Diagonal`s
