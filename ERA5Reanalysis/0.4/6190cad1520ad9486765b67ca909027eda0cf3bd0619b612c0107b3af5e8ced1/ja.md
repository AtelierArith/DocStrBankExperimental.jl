```
download(
    e5ds :: Union{ERA5Hourly,ERA5Monthly},
    evar :: SingleVariable,
    ereg :: ERA5Region;
    ispy :: Bool = false,
    overwrite :: Bool = false
) -> nothing
```

指定された単一レベル変数と地理的地域のために、CDSデータストアからERA5データをダウンロードします。 `ispy`を`true`に設定することで生成されたPythonスクリプトを使用してダウンロードするか、代わりにJuliaを直接使用することができます。

この機能を利用するには、CDSAPIをマシンにインストールし、CDSウェブサイトで利用規約に同意している必要があります。

# 引数

  * `e5ds` : 指定されたERA5データセット（時間別または月別）

      * `e5ds.start` は開始日を定義します
      * `e5ds.stop` は終了日を定義します
      * `e5ds.path` はすべての再解析データが保存されるパスを定義します
  * `evar` : ダウンロードする単一レベル変数を指定します
  * `ereg` : ダウンロードするデータの`GeoRegion`と解像度を指定します
  * `ipsy` : Juliaの代わりにデータをダウンロードするために使用できるPythonスクリプトを生成するかどうかを指定します
  * `overwrite` : デフォルトは`false`です。trueに設定すると、既存のデータが上書きされます。
