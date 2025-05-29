```
build_momenta(proc, model, Ptot::AbstractFourMomentum, out_psl::AbstractOutPhaseSpaceLayout, out_coords::Tuple)
```

与えられた相空間座標（`out_coords`）と総入射運動量（`Ptot`）を使用して、出力粒子の運動量を構築します。

この関数は、出力運動量がエネルギーと運動量の保存を満たすことを保証し、使用中の物理モデルと一致します。

# 引数

  * `proc`: 散乱過程の定義、[`AbstractProcessDefinition`](@ref)のサブタイプ。
  * `model`: 物理モデル、[`AbstractModelDefinition`](@ref)のサブタイプ。
  * `in_moms`: 入射四運動量、出力運動量を計算するために使用されます。
  * `out_psl`: 出力相空間レイアウト、[`AbstractOutPhaseSpaceLayout](@ref)のサブタイプ。
  * `out_coords`: 出力粒子の運動量をパラメータ化する相空間座標のタプル。

# 戻り値

  * 入射粒子を表す四運動量のコレクション。パフォーマンス上の理由から、四運動量の`Tuple`を返すことを推奨します。

```
