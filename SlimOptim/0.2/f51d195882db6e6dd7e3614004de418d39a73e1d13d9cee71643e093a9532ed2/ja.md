```
spg(funObj, x, funProj, options; ls=nothing, callback=nothing)
```

スペクトル投影勾配法を使用して、次の形式の問題を解決するための関数   min funObj(x) s.t. x in C

# 引数

  * `funObj(x)`: 最小化する関数（2番目の引数として勾配を返す）
  * `funProj(x)`: xをCに投影する関数
  * `x`: 初期推定値
  * `options`: spg_options構造体

# オプション引数

  * `ls` `: ユーザー提供の線形探索関数
  * `callback` : コールバック関数。入力として`result` callback(x::result)を受け取る必要があります

# 注意事項:

  * 投影の計算が高価な場合は、optionsでtestOptを0に設定することで投影の数を減らすことができます
  * minConf_SPGのmatlab実装から適応されました
