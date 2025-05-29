```
struct BeaTable
```

`bea_table` 呼び出しから返されたデータとメタデータを持つ BEA テーブル。

## フィールド

  * `dataset`: テーブルが取得されたデータセット
  * `table_number`: 非 API テーブル番号
  * `table_description`: テーブルに含まれるデータの説明
  * `metric`: データの測定指標、例：インデックス、ドルなど
  * `units`: 十億、百万など
  * `line_descriptions`: 行番号の説明を含む `DataFrame`
  * `table_notes`: テーブルに関するメモを含む `DataFrame`
  * `frequency`: (M)月次、(Q)四半期、または (A)年次
  * `data_startyear`: 返されたデータの最初の年（要求されたものと異なる場合があります）
  * `data_endyear`: 返されたデータの最後の年（要求されたものと異なる場合があります）
  * `api_tablename`: テーブルの `TableName` パラメータ値
  * `last_revised`: テーブルが最後に改訂された日付
  * `data_values`: テーブルデータ値を含む `DataFrame`
