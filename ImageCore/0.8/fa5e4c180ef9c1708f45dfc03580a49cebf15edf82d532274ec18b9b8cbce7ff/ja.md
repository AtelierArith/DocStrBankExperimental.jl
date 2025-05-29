```
scalesigned(min, center, max) -> f
```

値を範囲 `[min, center]` から `[-1,0]` に、`[center,max]` から `[0,1]` にスケーリングする関数 `f` を返します。`min`/`max` より小さい/大きい値は、それぞれ `min`/`max` にクランプされます。

参照: [`colorsigned`](@ref).
