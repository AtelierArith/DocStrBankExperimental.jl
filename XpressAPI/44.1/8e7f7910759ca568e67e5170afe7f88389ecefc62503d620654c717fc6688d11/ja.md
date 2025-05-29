```
XPRSnlpgetformularows(prob, rowind)::nformulas, rowind
```

非線形式の位置のリストを問題から取得します

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `rowind::AbstractVector{Int32}`: 非線形式の行位置を返すために使用される整数配列。この引数には `XPRS_ALLOC` を渡すことで、関数が適切なサイズの配列を自動的に割り当てることができます。

# 戻り値

  * `nformulas::Int32`: 問題内の非線形式の総数を返すために使用される整数。
  * `rowind::AbstractVector{Int32}`: 非線形式の行位置を返すために使用される整数配列。

C APIの対応する関数 [XPRSnlpgetformularows](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpgetformularows.html) のドキュメントも参照してください。
