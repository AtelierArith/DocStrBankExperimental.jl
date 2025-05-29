```
XPRSgetunbvec(prob)::seq
```

プライマルシンプレックスまたはデュアルシンプレックスアルゴリズムが行列がプライマルまたはデュアルで無限大であると判断する原因となるインデックスベクトルを返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。

# 戻り値

  * `seq::Int32`: 問題がプライマルまたはデュアルで無限大であると検出される原因となるベクトルが返される整数へのポインタ。

C APIの対応する関数[XPRSgetunbvec](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetunbvec.html)のドキュメントも参照してください。
