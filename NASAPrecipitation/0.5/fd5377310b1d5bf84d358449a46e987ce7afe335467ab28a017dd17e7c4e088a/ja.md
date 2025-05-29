```
TRMM3Hourly(
    ST = String,
    DT = Date;
    start :: TimeType,
    stop  :: TimeType,
    path  :: AbstractString = homedir(),
) -> npd :: TRMM3Hourly{ST,DT}
```

`npd`という`TRMM3Hourly`データセットを作成し、3時間ごとの出力の最終後処理実行からデータセットを取得します。

# キーワード引数

  * `start` : データセットのダウンロード/分析が始まる日付
  * `stop` : データセットのダウンロード/分析が終了する日付
  * `path` : データのダウンロード、保存、分析のために`trmm3hourly`フォルダが作成されるディレクトリ、デフォルトは`homedir()`によって呼び出されるホームディレクトリです。

`npd`の以下のフィールドは固定されます：

  * `ID` : trmm3hourly
  * `name` : 最終TRMM 3時間ごと
  * `doi` : 10.5067/TRMM/TMPA/3H/7
  * `hroot` : https://disc2.gesdisc.eosdis.nasa.gov/opendap/TRMM*L3/TRMM*3B42.7
  * `fpref` : 3B42
  * `fsuff` : 7.HDF

```
