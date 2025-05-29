```
build_momenta(proc::AbstractProcessDefinition, model::AbstractModelDefinition, in_psl::AbstractInPhaseSpaceLayout, in_coords::Real)
```

入射フェーズスペースレイアウト（`in_psl`）のための `build_momenta` のスカラー版で、フェーズスペース座標がタプルではなく単一のスカラーとして提供されます。

## 引数:

  * `proc`: 散乱過程の定義、[`AbstractProcessDefinition`](@ref) のサブタイプ。
  * `model`: 物理モデル、[`AbstractModelDefinition`](@ref) のサブタイプ。
  * `in_psl`: 入射フェーズスペースレイアウト、[`AbstractInPhaseSpaceLayout`](@ref) のサブタイプ。
  * `in_coords::Real`: 入射粒子のフェーズスペース座標を表す単一のスカラー。

## 戻り値:

  * 入射粒子を表す四元運動量のコレクション。パフォーマンスの理由から、四元運動量の `Tuple` を返すことが推奨されます。

## 注意事項:

この関数は `build_momenta` の便利なラッパーであり、スカラー `in_coords` を自動的に1タプルに変換します。入射フェーズスペースが粒子の運動量を定義するために単一の座標のみを必要とする場合に便利です。
