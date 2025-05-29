```
cg!(x, A, b; kwargs...) -> x, [history]
```

# 引数

  * `x`: 初期推定値で、インプレースで更新されます;
  * `A`: 線形演算子;
  * `b`: 右辺。

## キーワード

  * `statevars::CGStateVariables`: 中間結果を保持するために `x` に似た3つの配列を持ちます;
  * `initially_zero::Bool`: `true` の場合、`iszero(x)` を仮定し、初期残差ベクトルを計算する際に1つの行列-ベクトル積を保存できます;
  * `Pl = Identity()`: メソッドの左前処理器。`A` のように対称で正定値であるべきです;
  * `abstol::Real = zero(real(eltype(b)))`, `reltol::Real = sqrt(eps(real(eltype(b))))`: 停止条件 `|r_k| ≤ max(reltol * |r_0|, abstol)` のための絶対および相対許容誤差で、ここで `r_k ≈ A * x_k - b` は `k` 番目の反復における残差の近似です。

    !!! 注     真の残差ノルムは、パフォーマンスの理由から反復中に明示的に計算されることはありません; 丸め誤差が蓄積される可能性があります。
  * `maxiter::Int = size(A,2)`: 最大反復回数;
  * `verbose::Bool = false`: メソッド情報を印刷します;
  * `log::Bool = false`: 各反復における残差ノルムを追跡します。

# 出力

**`log` が `false` の場合**

  * `x`: 近似解。

**`log` が `true` の場合**

  * `x`: 近似解。
  * `ch`: 収束履歴。

**ConvergenceHistory キー**

  * `:tol` => `::Real`: 停止許容誤差。
  * `:resnom` => `::Vector`: 各反復における残差ノルム。
