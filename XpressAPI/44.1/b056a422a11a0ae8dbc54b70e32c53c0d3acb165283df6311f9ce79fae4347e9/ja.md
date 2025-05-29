```
XPRSsaveas(prob, sSaveFileName)::prob
```

現在のデータ構造、すなわち行列、制御設定、および問題属性設定をファイルに保存し、実行を終了して最適化を後で再開できるようにします。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `sSaveFileName::Union{Nothing,AbstractString}`: 保存するファイルの名前（.svfなし）。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSsaveas](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsaveas.html)のドキュメントも参照してください。
