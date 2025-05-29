```
IMERGLateHH(
    ST = String,
    DT = Date;
    start :: TimeType,
    stop :: TimeType,
    path :: AbstractString = homedir(),
) -> npd :: IMERGHalfHourly{ST,DT}
```

`IMERGHalfHourly` データセット `npd` を作成し、半時間ごとの出力のための近リアルタイム遅延処理ランからデータセットを取得します。

# キーワード引数

  * `start` : データセットのダウンロード / 分析が始まる日付
  * `stop` : データセットのダウンロード / 分析が終了する日付
  * `path` : データのダウンロード、保存、分析のために `imerglatehh` フォルダが作成されるディレクトリ、デフォルトは `homedir()` によって呼び出されるホームディレクトリです。

`npd` の以下のフィールドは固定されます。

  * `ID` : imerglatehh
  * `name` : Late IMERG Half-Hourly
  * `doi`   : 10.5067/GPM/IMERG/3B-HH-L/06
  * `hroot` : https://gpm1.gesdisc.eosdis.nasa.gov/opendap/GPM*L3/GPM*3IMERGHHL.06
  * `fpref` : 3B-HHR-L.MS.MRG.3IMERG
  * `fsuff` : V06B.HDF5

```
