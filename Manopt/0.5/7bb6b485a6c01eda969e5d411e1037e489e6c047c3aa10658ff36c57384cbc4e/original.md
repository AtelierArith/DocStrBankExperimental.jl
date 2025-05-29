```
get_gradient(TpM::TangentSpace, slso::SymmetricLinearSystemObjective, X)
get_gradient!(TpM::TangentSpace, Y, slso::SymmetricLinearSystemObjective, X)
```

evaluate the gradient of

$$
f(X) = \frac{1}{2} \lVert \mathcal A[X] + b \rVert_{p}^2,\qquad X ∈ T_{p}\mathcal M,
$$

Which is $\operatorname{grad} f(X) = \mathcal A[X]+b$. This can be computed in-place of `Y`.
