```
weighted_init([rng], [T], dims...;
    scaling=0.1, return_sparse=false)
```

重み付き入力層を表す行列を作成して返します。この初期化子は、範囲[-`scaling`, `scaling`]内で均等に分布したランダムな非ゼロ要素を持つ重み付き入力行列を生成します[^lu2017]。

# 引数

  * `rng`: ランダム数生成器。デフォルトはWeightInitializersの`Utils.default_rng()`です。
  * `T`: 貯水池行列の要素の型。デフォルトは`Float32`です。
  * `dims`: 行列の次元。`res_size x in_size`に従う必要があります。

# キーワード引数

  * `scaling`: 重み分布のスケーリングファクター。デフォルトは`0.1`です。
  * `return_sparse`: `sparse`行列を返すためのフラグ。デフォルトは`false`です。

# 例

```jldoctest
julia> res_input = weighted_init(8, 3)
6×3 Matrix{Float32}:
  0.0452399   0.0          0.0
 -0.0348047   0.0          0.0
  0.0        -0.0386004    0.0
  0.0         0.00981022   0.0
  0.0         0.0          0.0577838
  0.0         0.0         -0.0562827
```

[^lu2017]: Lu, Zhixin, et al. "Reservoir observers: Model-free inference of unmeasured variables in chaotic systems." Chaos: An Interdisciplinary Journal of Nonlinear Science 27.4 (2017): 041102.
