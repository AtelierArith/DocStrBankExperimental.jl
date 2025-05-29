```
UNIFACModel <: ActivityModel

UNIFAC2(components;
puremodel = PR,
userlocations = String[],
group_userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## 入力パラメータ

  * `R`: 単一パラメータ (`Float64`)  - 正規化されたグループのファン・デル・ワールス体積
  * `Q`: 単一パラメータ (`Float64`) - 正規化されたグループの表面積
  * `A`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - バイナリグループ相互作用エネルギーパラメータ
  * `B`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - バイナリグループ相互作用エネルギーパラメータ
  * `C`: ペアパラメータ (`Float64`, 非対称, デフォルトは `0`) - バイナリグループ相互作用エネルギーパラメータ

## 入力モデル

  * `puremodel`: 純粋な圧力依存特性を計算するためのモデル

## 説明

UNIFAC 2.0 活動モデル。修正された UNIFAC 2.0 (ドルトムント) の実装。メソッドは [`UNIFAC`](@ref) と同一ですが、行列補完法によってフィッティングされた新しいパラメータがあります。

## 参考文献

1. Hayer, N., Hasse, H., Jirasek, F., Modified UNIFAC 2.0 - A Group-Contribution Method Completed with Machine Learning. Arxive preprint (2024). [10.48550/arXiv.2412.12962](https://doi.org/10.48550/arXiv.2412.12962)

).
