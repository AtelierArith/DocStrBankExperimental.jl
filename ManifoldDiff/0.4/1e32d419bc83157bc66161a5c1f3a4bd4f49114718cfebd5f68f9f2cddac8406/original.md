```
riemannian_Hessian(M, p, eG, eH, X)
riemannian_Hessian!(M, Y, p, eG, eH, X)
```

Convert the Euclidean Hessian `eH=`$\operatorname{Hess} \tilde f(p) [X]$ of a function $f \colon \mathcal M \to \mathbb R$, which is the restriction of $\tilde f$ to $\mathcal M$, given additionally the (Euclidean) gradient $\operatorname{grad} \tilde f(p)$.

The Riemannian Hessian is then computed by

$$
\operatorname{Hess} f(p)[X]
= \operatorname{proj}_{T_p\mathcal M}\bigl(\operatorname{Hess} \tilde f(p)[X])
+ \mathcal W_p\Bigl( X, \operatorname{proj}_{N_p\mathcal M}\bigl( \operatorname{grad} \tilde f (p) \bigr) \Bigr),
$$

where $N_p\mathcal M$ denotes the normal space, i.e. the orthogonal complement of the tangent space in the embedding, and $\mathcal W_p$ denotes the [`Weingarten`](https://juliamanifolds.github.io/ManifoldsBase.jl/stable/functions/#ManifoldsBase.Weingarten-Tuple{AbstractManifold,%20Any,%20Any,%20Any}) map. See [Boumal:2023](@cite) for more details

The function is inspired by `ehess2rhess` in the [Matlab package Manopt](https://manopt.org).
