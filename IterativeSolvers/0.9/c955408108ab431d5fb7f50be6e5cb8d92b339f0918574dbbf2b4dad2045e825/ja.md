```
idrs!(x, A, b; s = 8, kwargs...) -> x, [history]
```

IDR(s)を用いて問題$Ax = b$を近似的に解きます。ここで、`s`はシャドウ空間の次元です。

# 引数

  * `x`: 初期推定値で、インプレースで更新されます;
  * `A`: 線形演算子;
  * `b`: 右辺。

## キーワード

  * `s::Integer = 8`: シャドウ空間の次元;
  * `Pl::precT`: 左前処理器,
  * `abstol::Real = zero(real(eltype(b)))`, `reltol::Real = sqrt(eps(real(eltype(b))))`: 停止条件`|r_k| ≤ max(reltol * |r_0|, abstol)`のための絶対および相対許容誤差。ここで、`r_k = A * x_k - b`は第`k`回の反残差です;
  * `maxiter::Int = size(A, 2)`: 最大反復回数;
  * `log::Bool`: 各反復での残差ノルムを追跡します;
  * `verbose::Bool`: 反復中に収束情報を印刷します。

# 戻り値

**`log`が`false`の場合**

  * `x`: 近似解。

**`log`が`true`の場合**

  * `x`: 近似解;
  * `history`: 収束履歴。
