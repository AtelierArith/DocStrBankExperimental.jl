```
XPRSgetobjdblcontrol(prob, objidx, control)::value
```

目的関数に関連付けられた特定のダブル制御パラメータの値を取得します。

これらのパラメータは、マルチオブジェクティブ最適化中に目的がどのように扱われるかを制御します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `objidx::Integer`: クエリする目的のインデックス。
  * `control::XPRSObjControl`: 値を返す制御パラメータ。

# 戻り値

  * `value::Float64`: 制御値が返されるダブルへのポインタ。

C APIの対応する関数[XPRSgetobjdblcontrol](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetobjdblcontrol.html)のドキュメントも参照してください。
