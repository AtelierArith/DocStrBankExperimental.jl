```
XPRSgetintcontrol(prob, control)::value
```

ユーザーがさまざまな整数制御パラメータの値を取得できるようにします。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `control::Integer`: 値を返す制御パラメータ。

# 戻り値

  * `value::Int32`: 制御の値が返される整数へのポインタ。

C APIの対応する関数のドキュメントも参照してください [XPRSgetintcontrol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetintcontrol.html)。
