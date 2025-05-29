```
get_Hessian(TpM::TangentSpace, slso::SymmetricLinearSystemObjective, X, V)
get_Hessian!(TpM::TangentSpace, W, slso::SymmetricLinearSystemObjective, X, V)
```

evaluate the Hessian of

$$
f(X) = \frac{1}{2} \lVert \mathcal A[X] + b \rVert_{p}^2,\qquad X ∈ T_{p}\mathcal M,
$$

Which is $\operatorname{Hess} f(X)[Y] = \mathcal A[V]$. This can be computed in-place of `W`.
