```
isboundary!(img::AbstractArray; background = 0, dims = coords_spatial(A), kwargs...)
```

各オブジェクトのちょうど内側にある境界を見つけ、元の画像を置き換えます。`background`は、境界としてマークされない背景ピクセルのスカラー値です。キーワード引数は`extreme_filter`に渡され、境界を発見する次元を示す`dims`が含まれます。

例については、アウトオブプレイスバージョンの[`isboundary`](@ref)を参照してください。
