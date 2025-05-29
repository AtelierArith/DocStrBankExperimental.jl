```
CellCache(grid::Grid)
CellCache(dh::AbstractDofHandler)
```

セルのノード、座標、および自由度のために事前に割り当てられたメモリを持つキャッシュオブジェクトを作成します。キャッシュは、`reinit!(cache, cellid)`を呼び出すことで新しいセルのために更新されます。ここで、`cellid::Int`はセルのIDです。

**`CellCache`を使用したメソッド**

  * `reinit!(cc, i)`: セル`i`のためにキャッシュを再初期化します
  * `cellid(cc)`: 現在キャッシュされているセルのIDを取得します
  * `getnodes(cc)`: セルのグローバルノードIDを取得します
  * `getcoordinates(cc)`: セルの座標を取得します
  * `celldofs(cc)`: セルのグローバル自由度IDを取得します
  * `reinit!(fev, cc)`: [`CellValues`](@ref)または[`FacetValues`](@ref)を再初期化します

[`CellIterator`](@ref)も参照してください。
