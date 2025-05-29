```
ERA5Monthly(;
    start :: TimeType,
    stop  :: TimeType,
    path  :: AbstractString = homedir(),
    hours :: Bool = false,
) -> ERA5Monthly <: ERA5Dataset or ERA5MonthlyHour <: ERA5Dataset
```

`ERA5Monthly` または `ERA5MonthlyHour` モジュールを、引数 `hours` に応じて作成する関数です。データは年ごとに保存されます。

# キーワード引数

  * `path` : データを保存する指定されたディレクトリ
  * `start` : ダウンロード/分析が始まる日付で、自動的に最も近い年に丸められます
  * `stop` : ダウンロード/分析が終了する日付で、自動的に最も近い年に丸められます
  * `hours` : false の場合、月次平均データをダウンロードします。true の場合、各時間の月次平均データをダウンロードします。
