```
minres!(x, A, b; kwargs...) -> x, [history]
```

(スキュー)エルミート行列 A に対して Ax = b を MINRES を使用して解きます。

# 引数

  * `x`: 初期推定値で、インプレースで更新されます;
  * `A`: 線形演算子;
  * `b`: 右辺。

## キーワード

  * `initially_zero::Bool = false`: `true` の場合、`iszero(x)` を仮定し、初期残差ベクトルを計算する際に行列-ベクトル積を 1 回保存できます;
  * `skew_hermitian::Bool = false`: `true` の場合、`A` がスキュー対称またはスキューエルミートであると仮定します;
  * `abstol::Real = zero(real(eltype(b)))`, `reltol::Real = sqrt(eps(real(eltype(b))))`: 停止条件 `|r_k| ≤ max(reltol * |r_0|, abstol)` のための絶対および相対許容誤差で、ここで `r_k = A * x_k - b` は `k` 回目の反復における残差です

    !!! 注     残差はおおよそしか計算されません。
  * `maxiter::Int = size(A, 2)`: 最大反復回数;
  * `log::Bool = false`: 各反復における残差ノルムを追跡します;
  * `verbose::Bool = false`: 反復中に収束情報を印刷します。

# 戻り値

**`log` が `false` の場合**

  * `x`: おおよその解。

**`log` が `true` の場合**

  * `x`: おおよその解;
  * `history`: 収束履歴。
