```
linesearch(ls, sol, d, f, g!, fg!, t, funRef, gtd, gvec)
```

Line search interface to LineSearches.jl

# 引数

  * `ls`: LineSearches.jl ドキュメントを参照してください
  * `f`: 目的関数, x -> f(x)
  * `g!``: 勾配をインプレースで計算する関数, x-> (g.= gradient(x))
  * `fg!``: 目的関数とインプレース勾配関数, x-> (f = f(x); g.= gradient(x))
  * `t`: 初期ステップ長の推測
  * `funRef`: 参照目的関数値
  * `gtd`: 参照方向の内積 dot(g0, d0)
  * `gvec`: 勾配用に事前割り当てされた配列
