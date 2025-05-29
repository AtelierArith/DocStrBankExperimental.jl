```
download(
    e5ds :: Union{ERA5Hourly,ERA5Monthly},
    evar :: Vector{SingleVariable},
    ereg :: ERA5Region;
    overwrite :: Bool = false
) -> nothing
```

指定された変数と地理的地域のためにCDSデータストアからERA5データをダウンロードします。このメソッドにはPythonオプションはありません。

この機能を利用するには、CDSAPIをマシンにインストールし、CDSウェブサイトで利用規約に同意している必要があります。

# 引数

  * `e5ds` : 指定されたERA5データセット（時間別または月別）

      * `e5ds.start` は開始日を定義します
      * `e5ds.stop` は終了日を定義します
      * `e5ds.path` はすべての再解析データが保存されるパスを定義します
  * `evar` : 一時ファイルにダウンロードされる単一レベル変数のベクトルを指定します。ダウンロードが完了すると、異なる変数が抽出され、それぞれのフォルダに保存されます。
  * `ereg` : ダウンロードされるデータの `GeoRegion` と解像度を指定します
  * `overwrite` : デフォルトは `false` です。trueに設定すると、既存のデータが上書きされます。
