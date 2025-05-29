```
footprint(geo::AbstractGeometry)
footprint(geos)
```

`geo`のフットプリントを返します。

デフォルトでは、これは[`bounds(geo)`](@ref)にフォールバックしますが、`geo`を完全に含む任意の単一の`GeometryEntity`である可能性があります。

コレクションまたはイテレータ`geos`のフットプリントは`bounds(geos)`です。
