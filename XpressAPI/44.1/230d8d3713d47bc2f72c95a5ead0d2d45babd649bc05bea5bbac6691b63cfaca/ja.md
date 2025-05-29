```
XPRSreaddirs(prob, filename)::prob
```

ツリー検索を指示するためのディレクティブファイルを読み込みます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `filename::Union{Nothing,AbstractString}`: ディレクティブを読み込むファイル名を含む、最大MAXPROBNAMELENGTH文字の文字列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSreaddirs](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSreaddirs.html)のドキュメントも参照してください。
