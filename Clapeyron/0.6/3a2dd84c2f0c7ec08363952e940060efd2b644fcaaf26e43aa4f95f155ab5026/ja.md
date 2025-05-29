```
ogUNIFACModel <: UNIFACModel

ogUNIFAC2(components;
puremodel = PR, 
userlocations = String[],
group_userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## 入力パラメータ

  * `R`: 単一パラメータ (`Float64`)  - 正規化されたグループのヴァン・デル・ワールス体積
  * `Q`: 単一パラメータ (`Float64`) - 正規化されたグループの表面積
  * `A`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - バイナリグループ相互作用エネルギーパラメータ

## 入力モデル

  * `puremodel`: 純粋な圧力依存特性を計算するためのモデル

UNIFAC 2.0 (UNIQUAC機能群活動係数) 活動モデル。元の定式化。メソッドは [`ogUNIFAC`](@ref) と同一ですが、行列補完法によってフィッティングされた新しいパラメータがあります。

## 参考文献

1. Hayer, N., Wendel, T., Mandt, S., Hasse, H., Jirasek, F., 機械学習による熱力学的グループ寄与法の進展: UNIFAC 2.0, Chemical Engineering Journal 504 (2025) 158667. [10.1016/j.cej.2024.158667](https://doi.org/10.1016/j.cej.2024.158667).
