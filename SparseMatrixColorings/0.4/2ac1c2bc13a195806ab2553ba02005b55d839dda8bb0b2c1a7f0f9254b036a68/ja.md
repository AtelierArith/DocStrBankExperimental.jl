```
DynamicDegreeBasedOrder{degtype,direction}(; reproduce_colpack=false)
```

動的に計算された次数を使用して頂点をソートする[`AbstractOrder`](@ref)のインスタンスです。

この順序は、動的次数に基づいて頂点をバケットに割り当て、その後、頂点をバケット間で移動させることによってバケットを反復的に更新することによって機能します。

# 型パラメータ

  * `degtype::Symbol`: `:forward`（前向き次数）または `:back`（後向き次数）を指定できます。
  * `direction::Symbol`: `:low2high`（順序が最小から最大、すなわち `1` から `n` に定義されている場合）または `:high2low`（順序が最大から最小、すなわち `n` から `1` に定義されている場合）を指定できます。

# 具体的なバリアント

  * [`IncidenceDegree`](@ref)
  * [`SmallestLast`](@ref)
  * [`DynamicLargestFirst`](@ref)

# 設定

  * `reproduce_colpack::Bool`: 元のColPack実装と全く同じ方法でバケットを管理するかどうか。

      * `reproduce_colpack=true`の場合、常にバケットの末尾で頂点を追加および削除します（片方向）。
      * `reproduce_colpack=false`（デフォルト）の場合、バケットの先頭または末尾のいずれかで頂点を追加および削除できます（双方向）。

バケットの両側での変更を許可することで、すべてのバケットに対して1つの固定サイズのベクターを使用し、バケットごとに動的サイズのベクターを使用する代わりに、ストレージの最適化が可能になります。その結果、デフォルト設定の `reproduce_colpack=false` はわずかにメモリ効率が良くなります。

# 参考文献

  * [*ColPack: Software for graph coloring and related problems in scientific computing*](https://dl.acm.org/doi/10.1145/2513109.2513110), Gebremedhin et al. (2013), セクション5
