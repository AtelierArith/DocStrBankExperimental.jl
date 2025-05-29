```
AugLagModel(model, y, μ, x, fx, cx)
```

与えられたモデル

$$
\min \ f(x) \quad s.t. \quad c(x) = 0, \quad l ≤ x ≤ u,
$$

この新しいモデルは、拡張ラグランジュ法のサブプロブレムを表します

$$
\min \ f(x) - yᵀc(x) + \tfrac{1}{2} μ \|c(x)\|^2 \quad s.t. \quad l ≤ x ≤ u,
$$

ここで、yはラグランジュ乗数ベクトルの推定値であり、μはペナルティパラメータです。

`meta`と`counters`を任意のNLPModelとして保持することに加えて、AugLagModelは次のものも保存します。

  * `model`: $f$、$c$、および境界を定義する内部モデル、
  * `y`: 乗数の推定値、
  * `μ`: ペナルティパラメータ、
  * `x`: 関数`c(x)`が計算された最後の点への参照、
  * `fx`: `f(x)`への参照、
  * `cx`: `c(x)`への参照、
  * `μc_y`: y - μ * cxのストレージ、
  * `store_Jv`および`store_JtJv`: `hprod!`で使用されるストレージ。

これらの値を更新するには、関数`update_cx!`、`update_y!`、および`update_μ!`を使用してください。
