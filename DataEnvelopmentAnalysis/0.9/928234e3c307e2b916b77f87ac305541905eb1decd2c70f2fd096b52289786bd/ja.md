```
DEAOptimizer(optimizer; time_limit, silent)
```

DEAオプティマイザの設定を格納するデータ構造。

# オプティマイザの仕様:

  * `LP`: 線形計画法のデフォルトオプティマイザ、GLPK。
  * `NLP`: 非線形計画法のデフォルトオプティマイザ、Ipopt。
  * JuMPがサポートする任意のソルバー。

# オプション引数

  * `time_limit=:60`: 秒単位の時間制限。
  * `silent=true`: オプティマイザの出力を抑制。
