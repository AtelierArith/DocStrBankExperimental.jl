```
randrange(X,Y,n; <keyword arguments>)
```

構造は、ttensorであるXとYのHadamard積(X ∗ Y)ₙのnモード行列化のランダム化範囲近似を利用しています。

### 引数:

  * `reqrank::Integer`: 要求されるランク。オプション。
  * `tol::Number/Vector`: 許容誤差。デフォルト: 1e-8。
  * `maxit`: 最大反復回数。デフォルト: 1000。
  * `r`: 停止基準のためのサンプル数。デフォルト: r=10。
  * `p::Integer`: オーバーサンプリングパラメータ。デフォルト: p=10。
