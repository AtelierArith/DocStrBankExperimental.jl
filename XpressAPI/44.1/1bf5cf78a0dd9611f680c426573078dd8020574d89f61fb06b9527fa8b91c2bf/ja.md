```
XPRSsetobjintcontrol(prob, objidx, control, value)::prob
```

目的に関連付けられた整数制御パラメータの値を設定します。

これらのパラメータは、マルチオブジェクティブ最適化中に目的がどのように扱われるかを制御します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `objidx::Integer`: 修正する目的のインデックス。
  * `control::XPRSObjControl`: 値を変更する制御パラメータ。
  * `value::Integer`: 制御パラメータを設定する値。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSsetobjintcontrol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsetobjintcontrol.html)のドキュメントも参照してください。
