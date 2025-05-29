```
get_Hessian(TpM::TangentSpace, slso::SymmetricLinearSystemObjective, X, V)
get_Hessian!(TpM::TangentSpace, W, slso::SymmetricLinearSystemObjective, X, V)
```

ヘッセ行列を評価します

$$
f(X) = \frac{1}{2} \lVert \mathcal A[X] + b \rVert_{p}^2,\qquad X ∈ T_{p}\mathcal M,
$$

これは $\operatorname{Hess} f(X)[Y] = \mathcal A[V]$ です。これは `W` のインプレースで計算できます。
