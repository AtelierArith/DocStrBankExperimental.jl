```julia
Invisible(x, y)

```

座標の範囲を `x, y` に拡張する唯一の機能を持つ不可視オブジェクトを作成します。`x, y` は `Interval` または `nothing` である必要があります。

また、`Invisible(bounds_xy(object)...)` を使用して、`object` にある範囲に拡張することもできますし、`Invisible(bounds_xy(object)[1], nothing)` を使用して `x` 軸のみを拡張することもできます。
