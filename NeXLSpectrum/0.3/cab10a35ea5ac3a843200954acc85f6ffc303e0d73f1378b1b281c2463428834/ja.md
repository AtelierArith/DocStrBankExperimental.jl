```
shannon_entropy(img::AbstractArray{Gray{N0f8}})
```

画像内のデータのlog2エントロピーを計算します。Images.jl 24.1のentropy(...)はバグがあり、25.0で削除されました。
