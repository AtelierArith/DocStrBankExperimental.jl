```julia
struct PlainMetisPartitioning <: ExtendableGrids.AbstractPartitioningAlgorithm
```

グリッドを `npart` パーティションに分割し、結果として得られたパーティション隣接グラフに色を付けます。これには、対応する拡張をトリガーするために Metis.jl をインポートする必要があります。

このアルゴリズムは、全体のパーティション数を制御することを可能にします。色ごとのパーティション数は、後続のパーティショングラフの色付けから来ており、現時点では制御できません。

パラメータ:

  * `npart::Int64`: パーティションの数 (デフォルト: 20)
