```
IMERGLateDY(
    ST = String,
    DT = Date;
    start :: TimeType,
    stop  :: TimeType,
    path :: AbstractString = homedir(),
) -> npd :: IMERGDaily{ST,DT}
```

`IMERGDaily` データセット `npd` を作成し、日次出力のための近リアルタイム遅延処理ランからデータセットを取得します。

# キーワード引数

  * `start` : データセットのダウンロード / 分析が始まる日付
  * `stop` : データセットのダウンロード / 分析が終了する日付
  * `path` : データのダウンロード、保存、分析のために `imerglatedy` フォルダが作成されるディレクトリ、デフォルトは `homedir()` によって呼び出されるホームディレクトリです。

`npd` の以下のフィールドは固定されます：

  * `ID` : imerglatedy
  * `name` : Late IMERG Daily
  * `doi`   : 10.5067/GPM/IMERGDL/DAY/06
  * `hroot` : https://gpm1.gesdisc.eosdis.nasa.gov/opendap/GPM*L3/GPM*3IMERGDL.06
  * `fpref` : 3B-DAY-L.MS.MRG.3IMERG
  * `fsuff` : S000000-E235959.V06.nc4

```
