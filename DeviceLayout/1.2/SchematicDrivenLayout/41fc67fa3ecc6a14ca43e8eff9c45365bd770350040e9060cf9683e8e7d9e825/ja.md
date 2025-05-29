```
render!(cs::AbstractCoordinateSystem, obj::GeometryEntity, meta::DeviceLayout.Meta,
    target::LayoutTarget; kwargs...)
```

`obj`を`cs`にレンダリングし、メタデータをレイヤーと`target`によるレンダリングオプションにマッピングします。
