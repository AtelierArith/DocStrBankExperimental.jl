```
SimpleWeightedEdge{T,U}
```

型 `T` のエッジの端点と型 `U<:Real` の重みを持つ重み付きエッジの具体的な構造体です。

# フィールド

  * `src::T`: エッジのソース
  * `dst::T`: エッジの宛先
  * `weight::U`: エッジの重み
