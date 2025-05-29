```
XPRSgetobjintcontrol(prob, objidx, control)::value
```

与えられた整数制御パラメータの値を取得します。これは目的に関連しています。

これらのパラメータは、マルチオブジェクティブ最適化中に目的がどのように扱われるかを制御します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `objidx::Integer`: クエリする目的のインデックス。
  * `control::XPRSObjControl`: 値を返す制御パラメータ。

# 戻り値

  * `value::Int32`: 制御値が返される整数へのポインタ。

C APIの対応する関数[XPRSgetobjintcontrol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetobjintcontrol.html)のドキュメントも参照してください。
