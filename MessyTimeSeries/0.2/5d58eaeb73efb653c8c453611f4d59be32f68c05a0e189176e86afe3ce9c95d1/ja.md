```
moving_block_bootstrap(Y::Union{FloatMatrix, JMatrix{Float64}}, subsample::Float64, samples::Int64, seed::Int64=1)
```

移動ブロックブートストラップサンプルを生成します。

移動ブロックブートストラップは、時系列を順序付けられた重複した連続観測のブロックにランダムにサブサンプリングします。

# 引数

  * `Y`: 観測された測定値（`nxT`）、ここで `n` は系列の数、`T` は観測の数です。
  * `subsample`: 観測期間の数に対するブロックサイズの割合。0と1の間に制限されています。
  * `samples`: ブートストラップサンプルの数。
  * `seed`: ランダムシード（デフォルト: 1）。

# 参考文献

Kunsch (1989) および Liu and Singh (1992)。
