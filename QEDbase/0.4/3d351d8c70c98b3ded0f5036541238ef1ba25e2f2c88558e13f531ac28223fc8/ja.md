```
build_momenta(proc, model, in_psl::AbstractInPhaseSpaceLayout, in_coords::Tuple)
```

与えられた相空間座標を使用して、入射粒子の運動量を構築します。

これは、内部で `_build_momenta` を呼び出し、座標の数を相空間の次元性に対して検証するユーザー向けの関数です。

# 引数

  * `proc`: 散乱過程の定義、[`AbstractProcessDefinition`](@ref) のサブタイプ。
  * `model`: 物理モデル、[`AbstractModelDefinition`](@ref) のサブタイプ。
  * `in_psl`: 入射相空間レイアウト、[`AbstractInPhaseSpaceLayout`](@ref) のサブタイプ。
  * `in_coords`: 入射粒子の運動量をパラメータ化する相空間座標のタプル。

# 戻り値

  * 入射粒子を表す四元運動量のコレクション。パフォーマンス上の理由から、四元運動量の `Tuple` を返すことを推奨します。
