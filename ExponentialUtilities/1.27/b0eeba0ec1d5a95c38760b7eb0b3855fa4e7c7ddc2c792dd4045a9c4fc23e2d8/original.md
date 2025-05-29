```
phi(z,k[;cache]) -> [phi_0(z),phi_1(z),...,phi_k(z)]
```

Compute the scalar phi functions for all orders up to k.

The phi functions are defined as

$$
\varphi_0(z) = \exp(z),\quad \varphi_{k+1}(z) = \frac{\varphi_k(z) - 1}{z}
$$

Instead of using the recurrence relation, which is numerically unstable, a formula given by Sidje is used (Sidje, R. B. (1998). Expokit: a software package for computing matrix exponentials. ACM Transactions on Mathematical Software (TOMS), 24(1), 130-156. Theorem 1).
