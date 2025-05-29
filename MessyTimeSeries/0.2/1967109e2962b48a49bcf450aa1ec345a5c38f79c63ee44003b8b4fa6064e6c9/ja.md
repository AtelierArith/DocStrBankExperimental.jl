```
block_jackknife(Y::Union{FloatMatrix, JMatrix{Float64}}, subsample::Float64)
```

ブロックジャックナイフ (Kunsch, 1989) サンプルを生成します。この実装は Pellegrino (2022) で説明されています。

この手法は、与えられたサイズの連続した観測のブロックを順番に削除することによって、時系列データセットをサブサンプリングします。

# 引数

  * `Y`: 観測された測定値 (`nxT`)、ここで `n` は系列の数、`T` は観測の数です。
  * `subsample`: 観測期間の数に対するブロックサイズの割合。0 と 1 の間に制限されています。

# 参考文献

Kunsch (1989) および Pellegrino (2022)。
