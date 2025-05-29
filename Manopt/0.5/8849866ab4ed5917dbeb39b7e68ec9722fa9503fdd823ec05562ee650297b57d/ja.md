```
ExactPenaltyGrad{S, CO, R}
```

[`ExactPenaltyCost`](@ref)に基づく勾配を表し、[`ConstrainedManifoldObjective`](@ref) `co`とパラメータ$ρ$、および追加のパラメータ$u$を使用するスムージング技術を用います。

この構造体は、両方の形式でファンクタでもあります。

  * `(M, p) -> X` は、割り当て方式で勾配を計算します。
  * `(M, X, p)` は、インプレース方式で勾配を計算します。

## フィールド

  * `ρ`、`u` は前述の通り
  * `co` 非滑らかな目的関数

## コンストラクタ

```
ExactPenaltyGradient(co::ConstrainedManifoldObjective, ρ, u; smoothing=LinearQuadraticHuber())
```
