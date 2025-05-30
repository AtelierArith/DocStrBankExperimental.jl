```
decompose(::Type{TargetType}, primitive)
decompose(::Type{TargetType}, data::AbstractVector)
```

与えられた型に依存して、プリミティブからデータを抽出し、そのeltypeを`TargetType`に変換します。

可能な`TargetType`s:

  * `<: Point` は位置を抽出して変換します（`coordinates()`を呼び出します）
  * `<: AbstractFace` は面を抽出して変換します（`faces()`を呼び出します）
  * `<: Normal{<: Vec}` は法線を抽出して変換します。必要に応じて生成します（`normals()`を呼び出します）
  * `<: UV{<: Vec}` は2Dテクスチャ座標を抽出して変換します。必要に応じて生成します（`texturecoordinates()`を呼び出します）
  * `<: UVW{<: Vec}` は3Dテクスチャ座標を抽出して変換します。必要に応じて生成します（`texturecoordinates()`を呼び出します）
