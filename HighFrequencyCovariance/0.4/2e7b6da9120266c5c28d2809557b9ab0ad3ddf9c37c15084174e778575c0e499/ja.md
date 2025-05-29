```
blockwise_estimation(ts::SortedDataFrame, blocking_frame::DataFrame)
```

一連の共分散推定を実行し、結果を結合します。入力として必要なものは、価格更新データを含むSortedDataFrameと、どの推定を実行するかを説明するデータフレームの2つです。これは、`put_assets_into_blocks_by_trading_frequency`によって出力される形式と同じである必要があります（ただし、実際の推定はその関数が出力するものとは異なるようにカスタマイズできます）。

### 入力

  * `ts` - ティックデータ。
  * `blocking_frame` - どの推定を行い、どの順序で行うかを表す`DataFrame`。これはしばしば`put_assets_into_blocks_by_trading_frequency`関数によって生成されたもの（そしてその後修正されたもの）です。

### 戻り値

  * `CovarianceMatrix`。
