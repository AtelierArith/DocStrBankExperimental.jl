```
BB([; cost, redundant])
```

標準最適基底 (BB)。

# キーワード引数

  * `cost::BBCost`: (デフォルト: `ShannonEntropyCost()`) BBのコスト関数。
  * `redundant::Bool`: (デフォルト: `false`) 実行されるウェーブレット変換が冗長であるかどうか。冗長なウェーブレット変換（SWTやACWTなど）を使用してLSDBを実行する場合は、`redundant=true`に設定します。

**参照:** [`BestBasisType`](@ref), [`LSDB`](@ref), [`JBB`](@ref)
