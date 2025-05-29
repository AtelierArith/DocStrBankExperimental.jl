```
XPRSsetobjdblcontrol(prob, objidx, control, value)::prob
```

与えられたダブル制御パラメータの値を目的に関連付けて設定します。

これらのパラメータは、マルチオブジェクティブ最適化中に目的がどのように扱われるかを制御します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `objidx::Integer`: 修正する目的のインデックス。
  * `control::XPRSObjControl`: 値を変更する制御パラメータ。
  * `value::Float64`: 制御パラメータを設定する値。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSsetobjdblcontrol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsetobjdblcontrol.html)のドキュメントも参照してください。
