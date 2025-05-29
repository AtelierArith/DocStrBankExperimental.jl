```
gmres!(x, A, b; kwargs...) -> x, [history]
```

再起動GMRESを用いて問題$Ax = b$を解きます。

# 引数

  * `x`: 初期推定値、インプレースで更新されます;
  * `A`: 線形演算子;
  * `b`: 右辺。

## キーワード

  * `initially_zero::Bool`: `true`の場合、`iszero(x)`を仮定し、初期残差ベクトルを計算する際に1回の行列-ベクトル積を保存できます;
  * `abstol::Real = zero(real(eltype(b)))`, `reltol::Real = sqrt(eps(real(eltype(b))))`: 停止条件`|r_k| ≤ max(reltol * |r_0|, abstol)`のための絶対および相対許容誤差、ここで`r_k = A * x_k - b`
  * `restart::Int = min(20, size(A, 2))`: 指定された反復回数の後にGMRESを再起動します;
  * `maxiter::Int = size(A, 2)`: GMRESの最大内反復回数;
  * `Pl`: 左前処理器;
  * `Pr`: 右前処理器;
  * `log::Bool`: 各反復で残差ノルムを追跡します;
  * `verbose::Bool`: 反復中に収束情報を印刷します。
  * `orth_meth::OrthogonalizationMethod = ModifiedGramSchmidt()`: 直交化法 (ModifiedGramSchmidt(), ClassicalGramSchmidt(), DGKS())

# 戻り値

**`log`が`false`の場合**

  * `x`: 近似解。

**`log`が`true`の場合**

  * `x`: 近似解;
  * `history`: 収束履歴。
