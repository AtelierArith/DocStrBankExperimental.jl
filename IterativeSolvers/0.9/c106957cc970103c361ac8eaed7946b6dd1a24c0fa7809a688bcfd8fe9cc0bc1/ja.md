```
qmr!(x, A, b; kwargs...) -> x, [history]
```

クワジミニマル残差（QMR）法を用いて問題 $Ax = b$ を解きます。

# 引数

  * `x`: 初期推定値で、インプレースで更新されます;
  * `A`: 線形演算子;
  * `b`: 右辺。

## キーワード

  * `initially_zero::Bool`: `true` の場合、`iszero(x)` を仮定し、初期残差ベクトルを計算する際に1つの行列-ベクトル積を保存できます;
  * `maxiter::Int = size(A, 2)`: 最大反復回数;
  * `abstol::Real = zero(real(eltype(b)))`, `reltol::Real = sqrt(eps(real(eltype(b))))`: 停止条件 `|r_k| ≤ max(reltol * |r_0|, abstol)` のための絶対および相対許容誤差で、ここで `r_k = A * x_k - b`
  * `log::Bool`: 各反復で残差ノルムを追跡します;
  * `verbose::Bool`: 反復中に収束情報を印刷します。

# 戻り値

**`log` が `false` の場合**

  * `x`: 近似解。

**`log` が `true` の場合**

  * `x`: 近似解;
  * `history`: 収束履歴。

[^Saad2003]: Saad, Y. (2003). Interactive method for sparse linear system.

[^Freund1990]: Freund, W. R., & Nachtigal, N. M. (1990). QMR : for a Quasi-Minimal Residual Linear Method Systems. (December).
