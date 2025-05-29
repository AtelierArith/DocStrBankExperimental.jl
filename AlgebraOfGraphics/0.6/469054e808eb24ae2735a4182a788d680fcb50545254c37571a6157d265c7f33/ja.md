```
draw(d; axis=NamedTuple(), figure=NamedTuple, palettes=NamedTuple())
```

[`AlgebraOfGraphics.AbstractDrawable`](@ref) オブジェクト `d` を描画します。実際には、`d` はしばしば [`AlgebraOfGraphics.Layer`](@ref) または [`AlgebraOfGraphics.Layers`](@ref) になります。出力は、`axis` に軸属性を、`figure` に図属性を、または `palettes` にカスタムパレットを指定することでカスタマイズできます。凡例とカラーバーは自動的に描画されます。より細かい制御が必要な場合は、[`draw!`](@ref)、[`legend!`](@ref)、および [`colorbar!`](@ref) を独立して使用してください。
