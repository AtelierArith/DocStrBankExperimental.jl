```julia
write_to_json(
    file::String,
    sol::HallThruster.Solution;
    average_start_time,
    save_time_resolved
)

```

`sol`を`file`に書き込みます。`file`がJSONファイルである場合。

## 必須引数

  * `file`: 解を記録するファイル
  * `sol`: 書き込む`Solution`オブジェクト

## オプションのキーワード引数

  * `average_start_time` = -1: 平均化が始まる時間。< 0の場合、平均化された出力は書き込まれません。
  * `save_time_resolved` = true: シミュレーションのすべてのフレームを保存するかどうか。`false`の場合、時間解像度の出力は書き込まれません。
