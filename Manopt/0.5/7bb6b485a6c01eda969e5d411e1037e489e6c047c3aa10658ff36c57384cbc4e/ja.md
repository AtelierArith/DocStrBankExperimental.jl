```
get_gradient(TpM::TangentSpace, slso::SymmetricLinearSystemObjective, X)
get_gradient!(TpM::TangentSpace, Y, slso::SymmetricLinearSystemObjective, X)
```

勾配を評価します

$$
f(X) = \frac{1}{2} \lVert \mathcal A[X] + b \rVert_{p}^2,\qquad X ∈ T_{p}\mathcal M,
$$

これは $\operatorname{grad} f(X) = \mathcal A[X]+b$ です。これは `Y` のインプレースで計算できます。
