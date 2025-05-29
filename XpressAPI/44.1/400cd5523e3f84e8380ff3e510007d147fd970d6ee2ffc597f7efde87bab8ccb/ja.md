```
XPRSwritedirs(prob, filename)::prob
```

現在の問題からディレクティブファイルにツリー検索ディレクティブを書き込みます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `filename::Union{Nothing,AbstractString}`: ディレクティブを書き込むファイル名を含む、最大MAXPROBNAMELENGTH文字の文字列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSwritedirs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSwritedirs.html)のドキュメントも参照してください。
