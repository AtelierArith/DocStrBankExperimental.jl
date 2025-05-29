```
XPRSscale(prob, rowscale, colscale)::prob
```

現在の行列を再スケーリングします。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `rowscale::AbstractVector{Integer}`: 行をスケーリングするための `2` の累乗を含むサイズ ROWS の整数配列、または必要ない場合は `nothing`。
  * `colscale::AbstractVector{Integer}`: 列をスケーリングするための `2` の累乗を含むサイズ COLS の整数配列、または必要ない場合は `nothing`。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C API の対応する関数 [XPRSscale](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSscale.html) のドキュメントも参照してください。
