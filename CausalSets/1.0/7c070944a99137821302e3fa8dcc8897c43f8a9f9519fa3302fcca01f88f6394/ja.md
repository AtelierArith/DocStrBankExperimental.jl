```
AbstractManifold{N}
```

`N`次元多様体のスーパタイプ。このタイプは、多様体のトポロジー、メトリック、および座標系を指定します。（現在、複数の座標系はサポートされていません）。

このタイプによって指定される多様体自体は無限に大きいため、有限の領域で作業するには、[`AbstractBoundary`](@ref) タイプを使用する必要があります。
