```julia
struct GumbelSoftmax <: DataDrivenLux.AbstractSimplex
```

`AbstractVector`を確率単体にマッピングするために、ガンベル分布のノイズを加え、各行に`softmax`を使用します。

# フィールド
