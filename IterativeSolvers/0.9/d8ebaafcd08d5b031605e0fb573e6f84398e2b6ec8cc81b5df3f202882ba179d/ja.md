```
chebyshev!(x, A, b, λmin::Real, λmax::Real; kwargs...) -> x, [history]
```

対称的で定義された行列 A に対して Chebyshev 反復を使用して Ax = b を解きます。

# 引数

  * `x`: 初期推定値で、インプレースで更新されます;
  * `A`: 線形演算子;
  * `b`: 右辺;
  * `λmin::Real`: 実固有値の下限
  * `λmax::Real`: 実固有値の上限

## キーワード

  * `initially_zero::Bool = false`: `true` の場合、`iszero(x)` を仮定し、初期残差ベクトルを計算する際に行列-ベクトル積を 1 回保存できます;
  * `abstol::Real = zero(real(eltype(b)))`, `reltol::Real = sqrt(eps(real(eltype(b))))`: 停止条件 `|r_k| ≤ max(reltol * |r_0|, abstol)` のための絶対および相対許容誤差で、ここで `r_k = A * x_k - b` は `k` 回目の反復における残差です;
  * `maxiter::Int = size(A, 2)`: GMRES の最大内部反復回数;
  * `Pl = Identity()`: 左前処理器;
  * `log::Bool = false`: 各反復における残差ノルムを追跡します;
  * `verbose::Bool = false`: 反復中に収束情報を印刷します。

# 戻り値

**`log` が `false` の場合**

  * `x`: 近似解。

**`log` が `true` の場合**

  * `x`: 近似解;
  * `history`: 収束履歴。
