```
LSDB([; cost, redundant])
```

最小統計依存基底 (LSDB)。

# キーワード引数

  * `cost::LSDBCost`: (デフォルト: `DifferentialEntropyCost()`) LSDBのコスト関数。
  * `redundant::Bool`: (デフォルト: `false`) 実行されるウェーブレット変換が冗長であるかどうか。冗長なウェーブレット変換（SWTやACWTなど）でLSDBを実行する場合は、`redundant=true`に設定します。

**関連情報:** [`BestBasisType`](@ref), [`JBB`](@ref), [`BB`](@ref)
