```
updateCarrierFreq!(pluto, value; doLog)
```

キャリア周波数を変更します。新しい有効周波数を表示します。

# 引数

  * `pluto::PlutoSDR` : 修正するラジオ。
  * `value::Int64` : 新しいキャリア周波数。

# キーワード

  * `doLog::Bool` : 新しいキャリア周波数の表示を切り替えます。

# 戻り値

  * `errno::Int` : 0 または負のエラーコード。
