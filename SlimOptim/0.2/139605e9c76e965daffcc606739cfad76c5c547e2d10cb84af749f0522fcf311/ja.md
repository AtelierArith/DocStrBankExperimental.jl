```
spg(f, g!, fg!, x, funProj, options; ls=nothing, callback=nothing)
```

スペクトル投影勾配法を使用して、min funObj(x) s.t. x in C の形式の問題を解くための関数

# 引数

  * `f(x)`: 最小化する関数（目的のみを返す）
  * `g!(g, x)`: 関数の勾配（インプレース）
  * `fg!(g, x)`: 目的と勾配（インプレース）
  * `funProj(x)`: x を C に投影する関数
  * `x`: 初期推定
  * `options`: spg_options 構造体

# オプション引数

  * `ls` `: ユーザー提供のラインサーチ関数
  * `callback` : コールバック関数。入力として `result` callback(x::result) を受け取る必要があります

# 注意:

  * 投影の計算が高価な場合は、options で testOpt を 0 に設定することで投影の回数を減らすことができます
  * minConf_SPG の matlab 実装から適応されました
