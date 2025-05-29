```
updateSamplingRate!(pluto, value; doLog)
```

サンプリングレートを変更します。新しい有効サンプリングレートを表示します。

# 引数

  * `pluto::PlutoSDR` : 修正するラジオ。
  * `value::Int64` : 新しいサンプリングレート。

# キーワード

  * `doLog::Bool` : 新しいキャリア周波数の表示を切り替えます。

# 戻り値

  * `errno::Int` : 0 または負のエラーコード。
