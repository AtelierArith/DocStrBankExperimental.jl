```
settimecol!(D::GMTdataset; col::Int=0, time_system="", time_unit="", time_epoch="")
```

`D` GMTdataset（またはGMTdatasetのベクトル）の時間列を指定された時間システムに設定します。

### 引数

  * `D``: GMTdatasetまたはGMTdatasetのベクトル

### キーワード引数

  * `col`: 時間列の列番号です。注意、これは必須のオプションです。もし`col`のみが提供された場合（すなわち、`time_xxx`オプションが使用されていない場合）、内部情報を設定して`col`を時間列にします。つまり、`col`にはすでに秒（Unix時間）での時間が含まれていると仮定します。
  * `time_system`: "JD"、"MJD"、"J2000"、"S1985"、"UNIX"、"RD0001"、"RATA"のいずれかです。これらのシステムの説明についてはGMTマニュアルを参照してください（https://docs.generic-mapping-tools.org/dev/gmt.conf.html#term-TIME_SYSTEM）。
  * `time_epoch`: `time_system`の代わりに`time_epoch`および`time_unit`オプションを使用します。`time_epoch`は'yyyy-mm-ddT[hh:mm:ss]'（グレゴリオ暦）または'yyyy-Www-ddT[hh:mm:ss]'（ISO）の形式の文字列です。
  * `time_unit`: "year"、"month"、"week"、"day"、"hour"、"minute"、"second"のいずれかです。
