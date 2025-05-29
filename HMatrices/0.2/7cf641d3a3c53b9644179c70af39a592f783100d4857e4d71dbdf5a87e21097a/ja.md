```
mutable struct ClusterTree{N,T}
```

`SVector{N,T}`のポイントを[`HyperRectangle`](@ref)sにクラスタリングするために使用されるツリー構造。

# フィールド:

  * `_elements::Vector{SVector{N,T}}` : ソートされた要素を含むベクター。
  * `container::HyperRectangle{N,T}` : 現在のノード内の要素のコンテナ。
  * `index_range::UnitRange{Int}` : 現在のノードに含まれる要素のインデックス。
  * `loc2glob::Vector{Int}` : ツリーの構築に使用された元の（グローバル）インデックスシステムへのローカルインデックスシステムからの置換。
  * `glob2loc::Vector{Int}` : `loc2glob`置換の逆。
  * `children::Vector{ClusterTree{N,T}}`
  * `parent::ClusterTree{N,T}`
