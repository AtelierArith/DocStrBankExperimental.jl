```
save_table(
    output_path::String
    MU::T,
) where T<:WiNDCtable
```

`WiNDCtable`をファイルに保存します。ファイル形式はHDF5で、他の言語でも開くことができます。ファイルは以下の構造を持ちます：

年 - DataFrame - `WiNDCtable`セットの各年のデータ - DataFrame - `WiNDCtable`列のセット - Array - 各年のDataFrameの列名

## 必要な引数

  * `output_path::String`: ファイルを保存するパス。
  * `MU::WiNDCtable`: 保存する`WiNDCtable`。
