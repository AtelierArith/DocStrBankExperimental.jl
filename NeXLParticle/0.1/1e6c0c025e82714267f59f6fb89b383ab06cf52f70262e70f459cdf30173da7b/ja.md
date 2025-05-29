```
multiternary(data::DataFrame, cols::AbstractArray{Symbol}, clscol::Union{Symbol, Missing}=missing; palette=TernPalette, norm=1.0)
```

`data`という`DataFrame`からシンプルなマルチターニャ図を描くためにCompose.jlを使用します。列は`cols`の順序で描画され、頂点は列の名前でラベル付けされます。
