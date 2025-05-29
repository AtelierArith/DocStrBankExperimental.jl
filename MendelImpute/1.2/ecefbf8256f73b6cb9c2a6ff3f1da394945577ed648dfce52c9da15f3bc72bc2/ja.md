```
convert_compressed(t<:Real, phaseinfo::String, reffile::String)
```

`phaseinfo`を完全な参照ハプロタイプパネル`H`を使用して、型`t`の位相遺伝子型行列に変換します。

# 入力

  * `t`: 行列の型。`bool`の場合、遺伝子型は`BitMatrix`に変換されます。
  * `phaseinfo`: `.jlso`形式で保存された`HaplotypeMosaicPair`のベクター
  * `reffile`: 完全な（非圧縮）ハプロタイプ参照ファイル

# 出力

  * `X1`: 位相遺伝子型のアレル1。各列はサンプルです。`X = X1 + X2`。
  * `X2`: 位相遺伝子型のアレル2。各列はサンプルです。`X = X1 + X2`。
  * `phase`: 位相付けと補完後の元のデータ構造。
  * `sampleID`: 各補完された人のID。
  * `H`: 完全な参照ハプロタイプパネル。`H`の列はハプロタイプです。
