```
exp(::LieGroup{ℝ, AdditionGroupOperation, Circle{ℝ}}, X)
exp!(::LieGroup{ℝ, AdditionGroupOperation, Circle{ℝ}}, g, X)
```

円群の[`LieAlgebra`](@ref)のベクトル`X`のリー群指数を計算します。これは$[-π, π)$の角度として表されます。この場合、リー代数は実数直線であり、ベクトル$X ∈ ℝ$のリー群指数はその同値類です。

$$
    \exp(X) = [X] ∈ \bigl\{ [x] ∈ ℝ / 2πℤ\ \big|\ x ∈ [-π,π)\bigr \}.
$$

これは`g`のインプレースで計算できます。
