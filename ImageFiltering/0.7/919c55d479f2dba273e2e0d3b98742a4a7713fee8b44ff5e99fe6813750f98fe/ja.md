```
padarray([T], img, border)
```

配列 `img` からパディングされた画像を生成し、境界条件と追加するパディングの量を指定する `border` を指定します。

パディングされた画像を返します。この関数は、1次元、2次元、または多次元の画像をサポートしています。出力画像の要素タイプ `T` を指定できます。

詳細については [`Pad`](@ref) と [`Fill`](@ref) を参照してください。

# 例

## パディング

`Pad` の主な構文は `(style, m, n, ...)` または `(style, (m, n))` であり、ここで `m` ピクセルが次元 1（上部と下部）に追加され、`n` ピクセルが次元 2 に追加されます。

左と右に 30、上と下に 40 を追加します：

```julia
padarray(A, Pad(:replicate, 30, 40))
padarray(A, Pad(:circular, 30, 40))
padarray(A, Pad(:symmetric, 30, 40))
padarray(A, Pad(:reflect, 30, 40))
```

上に 30、左に 40、下に 50、右に 60 を追加します：

```julia
padarray(A, Pad(0, (30, 40), (50, 60)))
padarray(A, Pad(0, (30, 40), (50, 60)))
```

# 3D

```julia
padarray(A, Pad(:replicate, 1, 1, 1)) 
padarray(A, Fill(0, (1, 1, 1))) 
```

## フィリング

`Fill` の主な構文は `(value, m, n)` または `(value, (m, n))` であり、画像は各次元で `m` ピクセルが前に追加され、`n` ピクセルが後ろに追加されます。

上に 20 の `-1` 値、左に 30、下に 40、右に 50 を追加します：

```julia
padarray(A, Fill(-1, (20, 30), (40, 50))) 
```
