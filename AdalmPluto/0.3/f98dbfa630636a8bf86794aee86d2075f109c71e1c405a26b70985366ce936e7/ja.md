```
updateBandwidth!(pluto, value)
```

帯域幅を変更します。新しい値を表示します。

# 引数

  * `pluto::PlutoSDR` : 修正するラジオ。
  * `value::Int64` : 新しいサンプリングレート。

# キーワード

  * `doLog::Bool` : 新しいキャリア周波数の表示を切り替えます。

# 戻り値

  * `errno::Int` : 0 または負のエラーコード。
