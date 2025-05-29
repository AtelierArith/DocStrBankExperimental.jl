```
log(::LieGroup{ℝ, AdditionGroupOperation, Circle{ℝ}}, g)
log!(::LieGroup{ℝ, AdditionGroupOperation, Circle{ℝ}}, X, g)
```

[`CircleGroup`](@ref circle-group-real)として表されるリー群の対数を計算します。角度は $[-π,π)$ の範囲です。[`LieAlgebra`](@ref) は実数直線であり、$\log$ は恒等写像によって与えられます。

形式的には、$\log$ は同値類 $[X]$ を代表元 $X∈ℝ$ に昇格させます。

これは `X` のインプレースで計算できます。
