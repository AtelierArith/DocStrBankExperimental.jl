```
uniform_partition(ranks,np,n[,ghost[,periodic]])
```

`LinearIndices(np)`のインデックスの`N`次元ブロックパーティションを生成します。ブロックサイズは（おおよそ）一定です。出力は、パーティションの各コンポーネントに含まれるインデックスを持つベクトルのベクトルです。結果の`eltype`は[`AbstractLocalIndices`](@ref)インターフェースを実装しています。

# 引数

  * `ranks`: ランクの分布を含む配列。
  * `np::NTuple{N}`: 各方向の部分の数。
  * `n::NTuple{N}`: 各方向のグローバルインデックスの数。
  * `ghost::NTuple{N}=ntuple(i->false,N)`: 各方向のゴーストインデックスの数。
  * `periodic::NTuple{N}=ntuple(i->false,N)`: 各方向の周期境界を使用するかどうか。

便利のために、スカラー入力をタプルの代わりに提供して1Dブロックパーティションを作成することもできます。この場合、引数`np`は省略可能で、`np=length(ranks)`として計算されます。現時点では、ゴーストインデックスの層はゼロ（`ghost=false`）または一（`ghost=true`）のみこの構文を使用することが可能です。より多くのゴーストインデックスが必要な場合は、代わりにタプルを使用してください。

# 例

ゴーストなしで4x4インデックスの2Dパーティションを2x2部分に分割

```jldoctest
julia> using PartitionedArrays

julia> rank = LinearIndices((4,));

julia> uniform_partition(rank,10)
4-element Vector{PartitionedArrays.LocalIndicesWithConstantBlockSize{1}}:
 [1, 2]
 [3, 4]
 [5, 6, 7]
 [8, 9, 10]

julia> uniform_partition(rank,(2,2),(4,4))
4-element Vector{PartitionedArrays.LocalIndicesWithConstantBlockSize{2}}:
 [1, 2, 5, 6]
 [3, 4, 7, 8]
 [9, 10, 13, 14]
 [11, 12, 15, 16]
```
