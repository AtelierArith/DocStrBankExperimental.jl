```
XPRSloadmipsol(prob, x)::status
```

最適化ツールに問題の開始MIPソリューションを読み込みます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `x::AbstractVector{Number}`: 変数の値を含むCOLSの長さのダブル配列（元の問題用であり、前処理問題用ではありません）。

# 戻り値

  * `status::Int32`: ステータスが返される`int`へのポインタ。

C APIの対応する関数のドキュメントも参照してください [XPRSloadmipsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadmipsol.html)。
