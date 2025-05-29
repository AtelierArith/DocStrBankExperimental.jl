```
makeauto(v::Vector{T};offset=nothing, firstindex=nothing, cutoff=0.0) where T
```

VectorからAutoVectorを作成し、新しいデータベクターを生成します。offsetが指定されている場合、データをoffsetだけ左にシフトします。firstindexが指定されている場合、mini=firstindexになります。offsetとfirstindexの両方を指定することはできません。cutoffが非ゼロの場合、要素はabs(el) > cutoffの場合にのみ追加されます。特定の範囲にVectorの一部を追加するには、たとえば、要素2から4を位置5から7に追加する場合、次のようにします: makeauto(v[2:4],firstindex=5)
