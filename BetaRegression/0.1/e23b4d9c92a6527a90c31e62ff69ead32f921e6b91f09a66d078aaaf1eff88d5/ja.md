```
fit(BetaRegressionModel, formula, data, link=LogitLink(), precisionlink=IdentityLink();
    kwargs...)
```

与えられたテーブル `data` に [`BetaRegressionModel`](@ref) をフィットさせます。`data` は任意の Tables.jl 互換テーブル（例：`DataFrame`）であり、与えられた `formula` を使用して構築できます。このメソッドでは、応答とモデル行列は式とテーブルから決定されます。明示的に提供することも可能です。

```
fit(BetaRegressionModel, X::AbstractMatrix, y::AbstractVector, link=LogitLink(),
    precisionlink=IdentityLink(); kwargs...)
```

提供されたモデル行列 `X` と応答ベクトル `y` を使用してベータ回帰モデルをフィットさせます。これらのメソッドの両方で、リンク関数を提供することができます。そうでない場合は、デフォルトのロジットリンクが使用されます。同様に、精度のリンクを提供することもできますが、そうでない場合はデフォルトの恒等リンクが使用されます。

## キーワード引数

  * `weights`: 重みのベクトルまたは `nothing`（デフォルト）。現在は `nothing` のみが受け入れられます。
  * `offset`: 線形予測子に加算されるオフセットベクトルまたは `nothing`（デフォルト）。
  * `maxiter`: フィッティング時に使用するフィッシャースコアリングの最大反復回数。デフォルトは 100。
  * `atol`: モデルの収束を確認する際に使用する絶対許容誤差。デフォルトは `sqrt(eps(T))` で、ここで `T` は推定値の型です。
  * `rtol`: 収束を確認する際に使用する相対許容誤差。デフォルトは `T` のための Base のデフォルト相対許容誤差です。

!!! tip
    収束の問題が発生した場合は、精度のために異なるリンクを試すことを検討してください。`LogLink()` は一般的な選択肢です。特に `Float32` を使用している場合は、最大反復回数を増やすことも有益です。

