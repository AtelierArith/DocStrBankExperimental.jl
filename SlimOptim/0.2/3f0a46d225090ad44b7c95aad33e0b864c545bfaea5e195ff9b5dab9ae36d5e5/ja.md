```
pqn(f, g!, fg!, x, projection, options; ls=nothing, callback=nothing)
```

制限付きメモリ投影準ニュートン法を使用して、次の形式の問題を解決するための関数   min objective(x) s.t. x in C

投影された準ニュートンのサブ問題は、スペクトル投影勾配アルゴリズムによって解決されます。

# 引数

  * `f(x)`: 最小化する関数（目的のみを返す）
  * `g!(g, x)`: 関数の勾配（インプレース）
  * `fg!(g, x)`: 目的と勾配（インプレース）
  * `funProj(x)`: xをCに投影する関数
  * `x`: 初期推定
  * `options`: pqn_options構造体

# オプション引数

  * `ls` `: ユーザー提供のラインサーチ関数
  * `callback` : コールバック関数。入力として`result` callback(x::result)を受け取る必要があります。

# 注意:

```
Adapted fromt he matlab implementation of minConf_PQN
```
