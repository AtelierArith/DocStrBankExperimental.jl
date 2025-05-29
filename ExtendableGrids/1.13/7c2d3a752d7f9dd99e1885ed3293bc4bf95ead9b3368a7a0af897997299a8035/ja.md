```
     partition(grid::ExtendableGrid,
               alg::AbstractPartitioningAlgorithm;
               nodes = false,
               keep_nodepermutation = false,
               edges = false )
```

`grid`のセルを`alg`に従ってパーティション分けし、パーティションの隣接グラフが色分けされるようにします。これにより、特定の色を持つすべてのパーティションは並行して処理できます。セルは再番号付けされ、特定のパーティションのセル番号は連続して番号付けされます。

結果のグリッドを返します。

並行FEMアセンブリおよびセル単位のFVMアセンブリに便利です。

キーワード引数:

  * `nodes`: trueの場合、セルのパーティショニングからノードのパーティショニングを誘導します。ノード/エッジ単位のFVMアセンブリに使用されます。さらに、結果のパーティショニングは`SparseMatrixCSC`を使用した並行行列-ベクトル積をサポートします。ノードは元のグリッドに対して再番号付けされます。`false`（デフォルト）の場合、すべてのノードがパーティション1に属し、他は空であるというトリビアルなノードのパーティショニングが作成されます。
  * `keep_nodepermutation`: trueの場合、`grid[`[`NodePermutation`](@ref)`]`内の元のグリッドに対するノードの順序を保持します。
  * `edges`: trueの場合、セルのパーティショニングからエッジのパーティショニングを誘導します。ノード/エッジ単位のFVMアセンブリに使用されます。このステップでは、比較的高価な追加の隣接関係が作成されます。`false`（デフォルト）の場合、すべてのエッジがパーティション1に属し、他は空であるというトリビアルなエッジのパーティショニングが作成されます。

アクセス:

  * [`pcolors`](@ref) はパーティションの色の範囲を返します
  * [`pcolor_partitions`](@ref) は特定の色のパーティション番号の範囲を返します
  * [`partition_cells`](@ref) は特定のパーティションのセル番号の範囲を提供します
  * [`partition_nodes`](@ref) は特定のパーティションのノード番号の範囲を提供します
  * [`partition_edges`](@ref) は特定のパーティションのエッジ番号の範囲を提供します

したがって、グリッドセルに対する並行ループは次のようになります。

```julia
for color in pcolors(grid)
    @threads for part in pcolor_partitions(grid, color)
                for cell in partition_cells(grid, part)
                 ...
                end
             end
end
```

`partition`を呼び出さない限り、これらの関数はトリビアルなデータを返すため、上記のサンプルコードは有効のままです。

!!! note
    `partition`は、グリッドの他の隣接関係を取得する前に呼び出す必要があります。


現在、パーティショニングは境界をカバーしておらず、境界セルは1つの大きなトリビアルパーティションに属します。 ```
