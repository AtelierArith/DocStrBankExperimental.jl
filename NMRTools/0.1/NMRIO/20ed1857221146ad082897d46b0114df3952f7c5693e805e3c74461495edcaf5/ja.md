```
FQList(values, unit::Symbol, relative::Bool)
```

周波数リストを表します。`unit` は `:Hz` または `:ppm` であり、`relative` は周波数がSFOに対して相対的に与えられているか（true）BFに対して相対的に与えられているか（false）を示します。

生の値は `data` 関数を使用して抽出できますが、（より良い方法として）絶対化学シフト（ppm単位）または相対オフセット（Hz単位）として [`getppm`](@ref) および [`getoffset`](@ref) 関数を使用して取得できます。

関連情報: [`getppm`](@ref), [`getoffset`](@ref).
