```
bregman(funobj, x, options)
```

線形化されたブレグマン反復法は、次のシステムに対して行われます。

$$
\frac{1}{2} ||TD \ x||_2^2 + λ ||TD \ x||_{1,w}  \ \ \ s.t Ax = b
$$

# 必要な引数

  * `funobj`: 目的値（`0.5 * norm(Ax-b)^2`）と勾配（`A'(Ax-b)`）を計算する関数
  * `x`: 初期推定値

# オプションの引数

  * `callback` : コールバック関数。入力として `result` コールバック(x::result)を受け取る必要があります。

# 非必須の引数

  * `options`: ブレグマンオプション、デフォルトは bregman_options(); options.TD はスパース化変換（例：カーブレット）を提供し、options.w は重み付き l1 のための重みベクトルを提供します。
