```
JBB([; cost, redundant])
```

ジョイントベストベース (JBB)。

# キーワード引数

  * `cost::JBBCost`: (デフォルト: `LoglpCost(2)`) JBBのコスト関数。
  * `redundant::Bool`: (デフォルト: `false`) 実行されるウェーブレット変換が冗長であるかどうか。冗長なウェーブレット変換（SWTやACWTなど）を使用してLSDBを実行する場合は、`redundant=true`に設定します。

**参照:** [`BestBasisType`](@ref), [`LSDB`](@ref), [`BB`](@ref)
