```
XPRSbasiscondition(prob)::cond, scaledcond
```

**非推奨**XPRSbasisstability関数を代わりに使用してください。

LP緩和を解いた後の現在の基底の条件数を計算します。

# 引数

  * `prob::XPRSprob`: 現在の問題。

# 戻り値

  * `cond::Float64`: 現在の基底の条件数。
  * `scaledcond::Float64`: スケーリングされた問題に対する現在の基底の条件数。

対応する関数[XPRSbasiscondition](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSbasiscondition.html)のC APIのドキュメントも参照してください。
