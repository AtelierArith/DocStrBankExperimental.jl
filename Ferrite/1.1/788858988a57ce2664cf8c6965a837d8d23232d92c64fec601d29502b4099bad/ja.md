```
InterfaceCache(grid::Grid)
InterfaceCache(dh::AbstractDofHandler)
```

インターフェースのノード、座標、およびdofのために事前に割り当てられたメモリを持つキャッシュオブジェクトを作成します。キャッシュは、`reinit!(cache, facet_a, facet_b)`を呼び出すことで新しいセルのために更新されます。ここで、`facet_a::FacetIndex`と`facet_b::FacetIndex`は2つのインターフェースファセットです。

**`InterfaceCache`の構造体フィールド**

  * `ic.a :: FacetCache`: インターフェースの最初のファセットのファセットキャッシュ
  * `ic.b :: FacetCache`: インターフェースの2番目のファセットのファセットキャッシュ
  * `ic.dofs :: Vector{Int}`: インターフェースのグローバルdof ID（`ic.a.dofs`と`ic.b.dofs`の和集合）

**`InterfaceCache`のメソッド**

  * `reinit!(cache::InterfaceCache, facet_a::FacetIndex, facet_b::FacetIndex)`: 新しいインターフェースのためにキャッシュを再初期化します
  * `interfacedofs(ic)`: インターフェースのグローバルdof IDを取得します

[`InterfaceIterator`](@ref)も参照してください。
