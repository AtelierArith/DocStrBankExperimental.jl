```
draw!(fig, d::AbstractDrawable; axis=NamedTuple(), palettes=NamedTuple())
```

[`AlgebraOfGraphics.AbstractDrawable`](@ref) オブジェクト `d` を `fig` に描画します。実際には、`d` はしばしば [`AlgebraOfGraphics.Layer`](@ref) または [`AlgebraOfGraphics.Layers`](@ref) になります。`fig` は、図、レイアウト内の位置、または `d` にファセット仕様がない場合の軸であることができます。出力は、`axis` に軸属性を指定したり、`palettes` にカスタムパレットを指定することでカスタマイズできます。
