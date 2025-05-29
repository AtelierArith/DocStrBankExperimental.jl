```
MBQCColouringSet
```

測定に基づく量子計算 (MBQC) モデルにおける着色セットを表す構造体です。2つのフィールドを含みます: `computation_round` と `test_round`。

# フィールド

  * `computation_round`: MBQC モデルにおける計算ラウンドを表します。
  * `test_round`: MBQC モデルにおけるテストラウンドを表します。

# 例

```julia
mbqc_colouring_set = MBQCColouringSet(computation_round, test_round)
```
