```
lsqr!(x, A, b; kwargs...) -> x, [history]
```

最小化 $\|Ax - b\|^2 + \|damp*x\|^2$ ユークリッドノルムにおいて。複数の解が存在する場合は、最小ノルム解を返します。

この手法は、Golub-Kahanの二重対角化プロセスに基づいています。これは、正規方程式 $(A^*A + λ^2I)x = A^*b$ にCGを適用することと代数的に同等ですが、特にAが条件不良な場合に数値的特性が優れています。

# 引数

  * `x`: 初期推定値で、インプレースで更新されます;
  * `A`: 線形演算子;
  * `b`: 右辺。

## キーワード

  * `damp::Number = 0`: ダンピングパラメータ。
  * `atol::Number = 1e-6`, `btol::Number = 1e-6`: 停止許容値。両方が1.0e-9（例えば）である場合、最終残差ノルムは約9桁の精度であるべきです。（最終的な `x` は通常、`cond(A)` とダンプのサイズに応じて、正しい桁数が少なくなります）。
  * `conlim::Number = 1e8`: 停止許容値。 `lsmr` は `cond(A)` の推定値が conlim を超えると終了します。互換性のあるシステム Ax = b の場合、conlim は1.0e+12（例えば）まで大きくすることができます。最小二乗問題の場合、conlim は1.0e+8未満であるべきです。最大の精度は `atol` = `btol` = `conlim` = ゼロに設定することで得られますが、その場合、反復回数が過剰になる可能性があります。
  * `maxiter::Int = maximum(size(A))`: 最大反復回数。
  * `verbose::Bool = false`: メソッド情報を印刷します。
  * `log::Bool = false`: メソッド実行の追加情報を含む `ConvergenceHistory` 型の追加要素を出力します。

# 戻り値

**`log` が `false` の場合**

  * `x`: 近似解。

**`log` が `true` の場合**

  * `x`: 近似解。
  * `ch`: 収束履歴。

**ConvergenceHistory キー**

  * `:atol` => `::Real`: atol 停止許容値。
  * `:btol` => `::Real`: btol 停止許容値。
  * `:ctol` => `::Real`: ctol 停止許容値。
  * `:anorm` => `::Real`: anorm。
  * `:rnorm` => `::Real`: rnorm。
  * `:cnorm` => `::Real`: cnorm。
  * `:resnom` => `::Vector`: 各反復における残差ノルム。
