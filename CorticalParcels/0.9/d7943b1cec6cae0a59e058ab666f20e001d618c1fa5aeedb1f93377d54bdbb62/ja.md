```
HemisphericParcellation{T}(surface, x)
```

`Vector` `x` から `HemisphericParcellation` を作成します。`x` の長さは、供給される `surface::Hemisphere` のサイズと一致する必要があります。その `Vector` の異なる要素が、結果の構造体の `Parcels` になります。パーセルは、型 `T` の ID によってキー付けされます。したがって、供給する `Vector` の eltype は `T` に強制変換可能でなければなりません。
