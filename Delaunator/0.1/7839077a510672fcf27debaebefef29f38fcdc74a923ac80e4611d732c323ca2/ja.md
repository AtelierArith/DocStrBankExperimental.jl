```
clippedpoly(p::InfinitePolygon, bbox; [closed=true])
clippedpoly!(pts, p::InfinitePolygon, bbox)
```

ポリゴンがバウンディングボックスの外に完全にある場合、空の配列を返します。それ以外の場合、バウンディングボックスにクリップされた無限ポリゴンのエッジを表す点の集合を返します。最初の点が最後の点と等しい場合、点の集合は閉じている（`closed=true`オプションが設定されている場合）ことになります。このオプションが設定されていなくても、点の集合は*閉じている*可能性があります。`closed=true`を使用すると、より単純な動作になります。この機能は、以下のようにミューテーションバージョンではオプションではありません。

ミューテーションバージョンは、次のようにして`pts`配列を更新します。

```
- `push!(pts, <newpt>)` 
- `last(pts)`
- `isempty(pts)`
```

入力タイプ`pts`を返します。

# 例コード

```
# デュアルセルのすべてのポリゴン領域を生成 
# ポイントバウンディングボックスの5%拡張にクリップ
# NaNで区切られたパスのリストとして、すべての 
# ポリゴンを閉じます。 
using GeometryBasics
t = triangulate(rand(Point2f, 15))
ppts = Point2f[]
for i in eachindex(t)
    ind = lastindex(ppts)
    clippedpoly!(ppts, dualcell(t, i), margin_bbox(t, 0.05))
    # ポリゴンが閉じているか確認... 
    if lastindex(ppts) > ind # それなら点を追加した
        if ppts[ind+1] != ppts[end] # 閉じているか確認
            push!(ppts, ppts[ind+1]) # ポリゴンを閉じる
        end 
    end 
    push!(ppts, (NaN,NaN)) # NaN区切りを追加 
end 
```

[`dualcell`](@ref)も参照してください。 
