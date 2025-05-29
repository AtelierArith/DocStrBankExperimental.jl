```
DynamicalDDEProblem{isinplace}(f1,f2,v0,u0,h,tspan,p=NullParameters(),callback=CallbackSet())
```

2つの関数 `f1` と `f2` から動的DDE問題を定義します。

# 引数

  * `f1` と `f2`: DDE内の関数。
  * `v0` と `u0`: 初期条件。
  * `h`: 初期履歴関数。
  * `tspan`: 問題の時間範囲。
  * `p`: `f1` と `f2` のパラメータ値。
  * `callback`: 問題を使用するすべてのソルバーに適用されるコールバック。デフォルトは何も指定されていません。

`isinplace` は、関数がインプレースかどうかをオプションで設定します。これは自動的に決定されますが、推測されることはありません。
