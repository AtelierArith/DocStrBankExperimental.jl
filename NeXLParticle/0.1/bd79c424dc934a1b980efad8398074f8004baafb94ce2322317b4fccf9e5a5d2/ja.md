```
blob(img::AbstractArray, thresh::Function)::Vector{Blob}
```

しきい値関数を満たす非連続領域を含む `Blob` のベクターを作成します。結果は `Blob` 面積でソートされています。
