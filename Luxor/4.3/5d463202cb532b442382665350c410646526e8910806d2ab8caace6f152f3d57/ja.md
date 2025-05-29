```
background(col::Colors.Colorant)
```

描画（または現在のクリッピング領域がある場合はその領域）を`color`で塗りつぶします。以前に描画されたグラフィックスは、色の不透明度に応じて完全にまたは部分的に隠されます。

背景を塗るために使用された色のタプル`(r, g, b, a)`を返します。

マクロ`@png`、`@draw`、および`@svg`は、描画のセットアップの一部として`background("white")`を使用します。

# 例:

```julia
background("antiquewhite")
background(1, 0.0, 1.0)
background(1, 0.0, 1.0, .5)
background(Luxor.Colors.RGB(0, 1, 0))
```

Colors.jlがインポートされている場合:

```julia
background(RGB(0, 1, 0))
background(RGBA(0, 1, 0))
background(RGBA(0, 1, 0, .5))
background(Luv(20, -20, 30))
```

PNG描画の背景色を指定しない場合、背景は透明になります。アルファ値を持つ色を渡すことで、PNGファイルの部分的または完全に透明な背景を設定できます。例えば、この「透明な黒」のように:

```julia
background(RGBA(0, 0, 0, 0))
```

または

```julia
background(0, 0, 0, 0)
```

背景を塗るために使用された色のタプル`(r, g, b, a)`を返します。
