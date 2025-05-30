```
SecondOrderDDEProblem{isinplace}(f,du0,u0,h,tspan,p=NullParameters(),callback=CallbackSet())
```

指定された関数で二次遅延微分方程式（DDE）問題を定義します。

# 引数

  * `f`: 二次導関数のための関数。
  * `du0`: 初期導関数。
  * `u0`: 初期条件。
  * `h`: 初期履歴関数。
  * `tspan`: 問題の時間範囲。
  * `p`: `f`のためのパラメータ値。
  * `callback`: 問題を使用するすべてのソルバーに適用されるコールバック。デフォルトは何も指定されていません。

`isinplace`は、関数がインプレースかどうかをオプションで設定します。これは自動的に決定されますが、推測されることはありません。
