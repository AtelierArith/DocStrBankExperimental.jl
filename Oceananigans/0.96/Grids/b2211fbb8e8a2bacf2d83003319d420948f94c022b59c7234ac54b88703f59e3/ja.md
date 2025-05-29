```
φnodes(grid::AbstractCurvilinearGrid, ℓx, ℓy, ℓz, with_halos=false)
```

曲線的な `grid` の内部ノードの位置を $φ$-方向で返します。位置は `ℓλ`, `ℓφ`, `ℓz` です。`Bounded` 方向の場合、`Face` ノードには境界点が含まれます。

例については [`znodes`](@ref) を参照してください。
