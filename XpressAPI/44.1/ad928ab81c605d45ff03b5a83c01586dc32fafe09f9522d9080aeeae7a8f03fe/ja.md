```
XPRSgetintattrib64(prob, attrib)::value
```

ユーザーがさまざまな整数問題属性の値を取得できるようにします。

問題属性は、問題の読み込みと最適化中に設定されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `attrib::Integer`: 値を返す問題属性。

# 戻り値

  * `value::Int64`: 問題属性の値が返される整数へのポインタ。

C APIの対応する関数[XPRSgetintattrib64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetintattrib64.html)のドキュメントも参照してください。
