```
XPRSoptimize(prob, flags)::solvestatus, solstatus
```

この関数は問題の最適解を探すための検索を開始します。

最適化の方向はOBJSENSEによって与えられます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `flags::Union{Nothing,AbstractString}`: `XPRSoptimize`に渡すフラグ（`OPTIMIZE`）。

# 戻り値

  * `solvestatus::Int32`: 終了後の解決ステータス。
  * `solstatus::Int32`: 終了後の解決状態。

C APIの対応する関数[XPRSoptimize](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSoptimize.html)のドキュメントも参照してください。
