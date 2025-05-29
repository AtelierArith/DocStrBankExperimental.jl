```
get_cost(TpM::TangentSpace, slso::SymmetricLinearSystemObjective, X)
```

evaluate the cost

$$
f(X) = \frac{1}{2} \lVert \mathcal A[X] + b \rVert_{p}^2,\qquad X ∈ T_{p}\mathcal M,
$$

at `X`.
