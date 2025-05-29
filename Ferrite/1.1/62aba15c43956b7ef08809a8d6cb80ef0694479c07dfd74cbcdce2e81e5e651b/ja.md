```
FacetCache(grid::Grid)
FacetCache(dh::AbstractDofHandler)
```

グリッド内の*ファセット*をループするのに適したセルのノード、座標、およびdofのために事前に割り当てられたメモリを持つキャッシュオブジェクトを作成します。キャッシュは、`reinit!(cache, fi::FacetIndex)`を呼び出すことで新しいファセットのために更新されます。

**`fc::FacetCache`を使用したメソッド**

  * `reinit!(fc, fi)`: ファセット`fi::FacetIndex`のためにキャッシュを再初期化します
  * `cellid(fc)`: 現在のcellidを取得します
  * `getnodes(fc)`: *セル*のグローバルノードIDを取得します
  * `getcoordinates(fc)`: *セル*の座標を取得します
  * `celldofs(fc)`: *セル*のグローバルdof IDを取得します
  * `reinit!(fv, fc)`: [`FacetValues`](@ref)を再初期化します

[`FacetIterator`](@ref)も参照してください。
