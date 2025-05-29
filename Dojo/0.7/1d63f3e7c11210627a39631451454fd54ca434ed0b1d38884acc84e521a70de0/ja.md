```
JointConstraint{T} <: Constraint{T}

2つのBodyオブジェクト間の平行移動および回転自由度を制限する制約。

id: 一意の識別番号
name: 一意の識別名
translational: 平行移動
rotational: 回転
spring: ジョイントスプリングのフラグ
damper: ジョイントダンパーのフラグ
parent_id: 親Body{T}の識別番号
child_id: 子Body{T}の識別番号
minimal_index: 最小座標のインデックス
impulses: 2つのBody{T}オブジェクト間の制約を維持するジョイントインパルス
```
