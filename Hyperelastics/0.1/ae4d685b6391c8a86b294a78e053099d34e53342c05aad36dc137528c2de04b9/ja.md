```julia
SussmanBathe(data; interpolant, k)

```

モデル:

  * 論文を参照

パラメータ:

  * なし

フィールド:

  * `data`: 補間を決定するために使用される超弾性一軸試験
  * `k`: モデルにおける総和の次数。
  * `interpolant`: 形式 `f(s, λ)` の関数で、関数 `f(λ) = s` を返します。

> Sussman T, Bathe KJ. A model of incompressible isotropic hyperelastic material behavior using spline interpolations of tension–compression test data. Communications in numerical methods in engineering. 2009 Jan;25(1):53-63.

