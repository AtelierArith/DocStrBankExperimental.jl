```
XPRS_bo_setpriority(bo, priority)::Nothing
```

ユーザー分岐オブジェクトの優先度値を設定します。

# 引数

  * `bo::XPRSbranchobject`: ユーザー分岐オブジェクト。
  * `priority::Integer`: 分岐オブジェクトに割り当てる新しい優先度値で、0から1000の範囲の数値でなければなりません。

C APIの対応する関数[XPRS*bo*setpriority](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRS_bo_setpriority.html)のドキュメントも参照してください。
