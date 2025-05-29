```
mapwindow!(f, out, img, window; border="replicate", indices=axes(img))
```

事前に割り当てられた出力を持つ [mapwindow](@ref) のバリアント。`out` と `img` が重複するメモリ領域を持つ場合、動作は未定義です。
