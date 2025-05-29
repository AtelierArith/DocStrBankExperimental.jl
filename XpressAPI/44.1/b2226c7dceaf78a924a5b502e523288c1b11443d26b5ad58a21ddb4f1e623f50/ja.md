```
XPRSsetprobname(prob, probname)::prob
```

現在のデフォルトの問題名を設定します。

このコマンドはめったに使用されません。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `probname::Union{Nothing,AbstractString}`: 問題名を含む最大MAXPROBNAMELENGTH文字の文字列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSsetprobname](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsetprobname.html)のドキュメントも参照してください。
