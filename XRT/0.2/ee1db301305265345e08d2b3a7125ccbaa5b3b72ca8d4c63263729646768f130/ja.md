```Julia
sync!(b::AbstractBOArray, direction::XRTWrap.BOSyncDirection.Type)
sync!(w::AbstractSyncDirectionWrapper, direction::XRTWrap.BOSyncDirection.Type)

```

指定された方向でバッファの内容を同期します。特定の同期方向を禁止するために、タイプに同期方向を持つ `BOArray` または `Array` を使用してください。
