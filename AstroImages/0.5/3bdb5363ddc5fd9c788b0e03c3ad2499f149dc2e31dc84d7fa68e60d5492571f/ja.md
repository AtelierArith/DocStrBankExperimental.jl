```
pix_to_world(img::AstroImage, pixcoords; all=false)
```

与えられた天文画像に対して、`pixcoords`で指定されたピクセルの世界座標を調べます。世界座標はWCS.jlを使用して解決され、`img`に存在する任意のFITSヘッダーから計算されたWCSTransformを使用します。ヘッダーにWCS情報がない場合、またはすべての軸が線形の場合、これは単にピクセル座標を返します。

`pixcoords`は、画像の現在の選択内の座標である必要があります。たとえば、次のようにスライスを選択した場合：

```julia-repl
julia> cube = load("some-3d-cube.fits")
julia> slice = cube[10:20, 30:40, 5]
```

次に、`slice`の左下隅のピクセルの座標を調べるには、次のように実行します：

```julia-repl
julia> world_coords = pix_to_world(img, [1, 1])
[10, 30]
```

`cube`のヘッダーにWCS情報が存在する場合、これらの座標はそれぞれ軸1、2、3を使用して解決されます。

すべての軸の世界座標を含めるには、`all=true`を渡します。

```julia-repl
julia> world_coords = pix_to_world(img, [1, 1], all=true)
[10, 30, 5]
```

!! 座標は`dims(img)`の順序で提供する必要があります。画像を転置した場合、座標を渡す順序は変更しないでください。
