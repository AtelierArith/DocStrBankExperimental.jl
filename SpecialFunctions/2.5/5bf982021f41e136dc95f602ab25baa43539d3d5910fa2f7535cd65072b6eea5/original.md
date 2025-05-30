```
gamma_inc_inv_qsmall(a, q, qgammaxa)
```

Compute `x0` - initial approximation when `q` is small from $e^{-x_{0}} x_{0}^{a} = q \Gamma(a)$. Asymptotic expansions Eqn (2.29) in the paper is used here and higher approximations are obtained using

$$
x \sim x_{0} - L + b \sum_{k=1}^{\infty} d_{k}/x_{0}^{k}
$$

where $b = 1-a$, $L = \ln{x_0}$.
