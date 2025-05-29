```
XPRSloadlpsol(prob, x, slack, duals, djs)::status
```

問題のLPソリューションをオプティマイザにロードします。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `x::AbstractVector{Number}`: オプション: 変数の値を含むCOLSの長さのダブル配列（元の問題用であり、前処理問題ではありません）。
  * `slack::AbstractVector{Number}`: オプション: スラック変数の値を含むROWSの長さのダブル配列。
  * `duals::AbstractVector{Number}`: オプション: 双対変数の値を含むROWSの長さのダブル配列。
  * `djs::AbstractVector{Number}`: オプション: 削減コストの値を含むCOLSの長さのダブル配列。

# 戻り値

  * `status::Int32`: ステータスが返される`int`へのポインタ。

C APIの対応する関数[XPRSloadlpsol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSloadlpsol.html)のドキュメントも参照してください。
