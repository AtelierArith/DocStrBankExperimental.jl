```
Grid{dim, C<:AbstractCell, T<:Real} <: AbstractGrid}
```

`Grid`は計算領域をカバーする`Ferrite.AbstractCell`と`Ferrite.Node`のコレクションです。境界条件を適用したり、サブドメインを定義するための補助構造体は、`cellsets`、`nodesets`、`facetsets`、および`vertexsets`に集められています。

# フィールド

  * `cells::Vector{C}`: グリッドのすべてのセルを格納します
  * `nodes::Vector{Node{dim,T}}`: グリッドの`dim`次元のノードを格納します
  * `cellsets::Dict{String, OrderedSet{Int}}`: `String`キーをセルIDの`OrderedSet`にマッピングします
  * `nodesets::Dict{String, OrderedSet{Int}}`: `String`キーをグローバルノードIDの`OrderedSet`にマッピングします
  * `facetsets::Dict{String, OrderedSet{FacetIndex}}`: `String`を`FacetIndex`の`OrderedSet`にマッピングします
  * `vertexsets::Dict{String, OrderedSet{VertexIndex}}`: `String`キーを`VertexIndex`の`OrderedSet`にマッピングします
