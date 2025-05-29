```
variable_partition(n_own,n_global[;start])
```

範囲 `1:n` の1D可変サイズブロックパーティションを構築します。出力は、パーティションの各コンポーネントに含まれるインデックスを持つベクトルのベクトルです。結果の `eltype` は [`AbstractLocalIndices`](@ref) インターフェースを実装しています。

# 引数

  * `n_own::AbstractArray{<:Integer}`: 各部分のブロックサイズを含む配列。
  * `n_global::Integer`: グローバルインデックスの数。`sum(n_own)` と等しくする必要があります。
  * `start::AbstractArray{Int}=scan(+,n_own,type=:exclusive,init=1)`: 各部分の最初のグローバルインデックス。

ユーザーに `n_global` と（オプションで）`start` を提供するように求めます。これらを発見するには通信が必要です。

# 例

```jldoctest
julia> using PartitionedArrays

julia> rank = LinearIndices((4,));

julia> n_own = [3,2,2,3];

julia> variable_partition(n_own,sum(n_own))
4-element Vector{PartitionedArrays.LocalIndicesWithVariableBlockSize{1}}:
 [1, 2, 3]
 [4, 5]
 [6, 7]
 [8, 9, 10]
```
