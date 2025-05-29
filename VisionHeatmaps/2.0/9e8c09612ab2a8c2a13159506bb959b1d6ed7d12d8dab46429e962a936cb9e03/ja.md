```
heatmap(x::AbstractArray)
heatmap(x::AbstractArray, pipeline)
heatmap(x::AbstractArray, image)
heatmap(x::AbstractArray, image, pipeline)
```

4D配列をヒートマップとして視覚化します。入力配列の次元はWHCN（幅、高さ、カラーチャンネル、バッチ次元）を仮定しています。
