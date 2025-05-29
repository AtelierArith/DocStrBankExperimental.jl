```
bicgstabl!(x, A, b, l; kwargs...) -> x, [history]
```

# 引数

  * `A`: 線形演算子;
  * `b`: 右辺（ベクトル）;
  * `l::Int = 2`: GMRESステップの数。

## キーワード

  * `max_mv_products::Int = size(A, 2)`: 行列ベクトル積の最大数。

BiCGStab(l)にとって、これは「反復回数」という用語よりも疑わしくない用語です;

  * `Pl = Identity()`: メソッドの左前処理器;
  * `abstol::Real = zero(real(eltype(b)))`, `reltol::Real = sqrt(eps(real(eltype(b))))`: 停止条件 `|r_k| ≤ max(reltol * |r_0|, abstol)` のための絶対および相対許容誤差。ここで、`r_k ≈ A * x_k - b` は `k` 番目の反復における近似残差です;

    !!! 注     1. 真の残差ノルムは反復中に計算されることはなく、近似値のみが計算されます;     2. 左前処理器が与えられた場合、停止条件は*前処理された残差*に基づいています。

# 戻り値

**`log` が `false` の場合**

  * `x`: 近似解。

**`log` が `true` の場合**

  * `x`: 近似解;
  * `history`: 収束履歴。
