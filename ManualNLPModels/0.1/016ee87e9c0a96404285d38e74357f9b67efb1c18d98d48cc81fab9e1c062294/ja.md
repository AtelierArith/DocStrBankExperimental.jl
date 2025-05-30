```
nlp = NLPModel(x, f; kwargs...)
nlp = NLPModel(x, lvar, uvar, f; kwargs...)
```

非線形最適化モデルを作成します。目的関数は `f` で、開始点は `x`、変数の下限は `lvar`、上限は `uvar` です（提供されている場合）。キーワード引数で追加の関数を提供できます。受け入れられる関数名とそのシグネチャのリストは以下の通りです：

制約のない場合：

  * `grad = (gx, x) -> gx`: `x` における `f` の勾配。`gx` に格納されます。
  * `objgrad = (gx, x) -> (f, gx)`: `f` と `x` における `f` の勾配。`gx` に格納されます。
  * `hprod = (hv, x, v; obj_weight=1) -> ...`: `x` におけるヘッセ行列とベクトル `v` の積。`hv` に格納されます。
  * `hess_coord = (rows, cols, (vals, x; obj_weight=1) -> ...)`: トリプレット形式の `x` におけるスパースヘッセ行列。

制約のある場合：

  * `cons = ((cx, x) -> ..., lcon, ucon)`: `x` における制約。`cx` に格納されます。`lcon` と `ucon` は制約の境界です。
  * `jprod = (jv, x, v) -> ...`: `x` におけるヤコビ行列とベクトル `v` の積。`jv` に格納されます。
  * `jtprod = (jtv, x, v) -> ...`: `x` における転置ヤコビ行列とベクトル `v` の積。`jtv` に格納されます。
  * `jac_coord = (rows, cols, (vals, x) -> ....)`: トリプレット形式の `x` におけるスパースヤコビ行列。
  * `hprod = (hv, x, y, v; obj_weight=1) -> ...`: `(x, y)` におけるラグランジアンヘッセ行列とベクトル `v` の積。`hv` に格納されます。
  * `hess_coord = (rows, cols, (vals, x, y; obj_weight=1) -> ...)`: トリプレット形式の `(x,y)` におけるスパースラグランジアンヘッセ行列。
