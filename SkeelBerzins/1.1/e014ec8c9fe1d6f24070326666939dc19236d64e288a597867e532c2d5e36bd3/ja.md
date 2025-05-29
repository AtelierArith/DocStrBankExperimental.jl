```
pdeval(m, xmesh, u_approx, x_eval, pb)
```

関数は、ソルバ関数 [`pdepe`](@ref) によって得られた解を空間成分に関して補間します。

入力引数:

  * `m`: 問題の対称性 (m=0,1,2 は直交、円筒、または球面を表します)。
  * `xmesh`: 空間の離散化。
  * `u_approx`: ソルバ `pdepe` によって得られた近似解。
  * `x_eval`: 近似解を補間する点または点のベクトル。
  * `pb`: 問題定義を定義する構造体、詳細は [`SkeelBerzins.ProblemDefinition`](@ref) を参照。

`x_eval` で評価された解とその空間成分に関する偏導関数に対応するタプル $(u,dudx)$ を返します。
