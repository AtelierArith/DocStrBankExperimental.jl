```
VectorPupilFunction(nₐ::Real, λ::Real, n_medium::Real, n_coverslip::Real, n_immersion::Real, grid_size::Integer)
```

空のフィールドコンポーネントを持つベクトル開口関数を作成します。

# 引数

  * `nₐ`: 数値開口
  * `λ`: 波長（μm単位）
  * `n_medium`: サンプル媒体の屈折率
  * `n_coverslip`: カバーガラスの屈折率
  * `n_immersion`: 没入媒体の屈折率
  * `grid_size`: 開口グリッドのサイズ（grid*size × grid*size）

# 戻り値

  * ゼロ初期化されたフィールドコンポーネントを持つ`VectorPupilFunction`
