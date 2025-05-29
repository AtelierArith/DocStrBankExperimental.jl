```
PolyArea(outer)
PolyArea([outer, inner₁, inner₂, ..., innerₖ])
```

`outer` リングを持つ多角形の面積と、オプションの内側リング `inner₁`、`inner₂`、...、`innerₖ`。

リングは [`Point`](@ref) のベクターまたは便利のために座標を持つタプルのベクターであることができ、その場合、最初の点はベクターの最後で *繰り返されてはいけません*。
