```
scalesigned(min, center, max) -> f
```

値を範囲 `[min, center]` から `[-1,0]` に、範囲 `[center,max]` から `[0,1]` にスケーリングする関数 `f` を返します。 `min` / `max` より小さい値は、それぞれ `min` / `max` にクランプされます。

参照: [`colorsigned`](@ref).
