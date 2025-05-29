```
KMeansTreeNode{T} <: AbstractNode
```

は、[K-Meansクラスタリングツリー](@ref)の各ノードのデータ型です。

# フィールド

  * `parent::Union{KMeansTreeNode{T},Nothing}`: 表されるクラスタの上位クラスタ
  * `children::Union{Vector{KMeansTreeNode{T}}, Nothing}`: 表されるクラスタに直接従属するすべてのクラスタ
  * `level::Integer`: 表されるクラスタのレベル
  * `center`: クラスタが定義される中心
  * `radius`: 中心と最も遠い点とのユークリッド距離
  * `data::T`: このクラスタ内の点のインデックスを含む配列
