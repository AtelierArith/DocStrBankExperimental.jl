```
XPRSsetdefaults(prob)::prob
```

すべてのコントロールをデフォルト値に設定します。

XPRSreadprob、XPRSloadmip、XPRSloadlp、XPRSloadmiqp、XPRSloadqpによって問題が読み込まれる前に呼び出す必要があります。

# 引数

  * `prob::XPRSprob`: 現在の問題。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSsetdefaults](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsetdefaults.html)のドキュメントも参照してください。
