```
XPRSsetlogfile(prob, filename)::prob
```

これはすべてのオプティマイザ出力をログファイルに向けます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `filename::Union{Nothing,AbstractString}`: すべてのログ出力が書き込まれるファイル名を含む、最大MAXPROBNAMELENGTH文字の文字列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSsetlogfile](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsetlogfile.html)のドキュメントも参照してください。
