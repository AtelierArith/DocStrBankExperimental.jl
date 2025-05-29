```
OceanGrid(elon::T, elat::U, edepth::V; R=6371.0u"km") where {T<:TU, U<:TU, V<:TU}
```

`elon`、`elat`、および `edepth` ベクトルによって定義されたボックスのエッジを持つ `OceanRectilinearGrid` を返します。地球の半径はキーワード `R` で変更できます（デフォルト値は6371 km）。湿ったボックスの3D配列 `wet3D` はデフォルトでどこでも真です。
