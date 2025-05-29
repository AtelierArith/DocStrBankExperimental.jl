```
ERA5Daily(;
    start :: TimeType,
    stop  :: TimeType,
    path  :: AbstractString = homedir(),
) -> ERA5Daily <: ERA5Dataset
```

`ERA5Hourly` モジュールを作成する関数です。すべての可能な時間がダウンロードされ、データは月ごとに保存されます。

# キーワード引数

  * `path` : データを保存する指定されたディレクトリ
  * `start` : ダウンロード/分析が始まる日付で、最寄りの月に自動的に丸められます
  * `stop` : ダウンロード/分析が終了する日付で、最寄りの月に自動的に丸められます
