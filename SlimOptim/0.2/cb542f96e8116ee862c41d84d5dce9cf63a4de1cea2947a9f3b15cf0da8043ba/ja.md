```
pqn(objective, x, projection, options; ls=nothing, callback=nothing)
```

目的関数を最小化するために制限付きメモリ投影準ニュートン法を使用する関数   min objective(x) s.t. x in C

投影準ニュートンのサブ問題は、スペクトル投影勾配アルゴリズムによって解決されます。

# 引数

  * `funObj(x)`: 最小化する関数（2番目の引数として勾配を返す）
  * `funProj(x)`: xをCに投影する関数
  * `x`: 初期推定値
  * `options`: pqn_options構造体

# オプション引数

  * `ls` `: ユーザー提供のラインサーチ関数
  * `callback` : コールバック関数。入力として`result` callback(x::result)を受け取る必要があります。

# 注意:

```
Adapted fromt he matlab implementation of minConf_PQN
```
