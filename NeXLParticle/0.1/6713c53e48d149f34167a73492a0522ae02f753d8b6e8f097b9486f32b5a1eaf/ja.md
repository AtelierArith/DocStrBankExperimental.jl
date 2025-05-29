```
rca(img::AbstractArray, search::Function, measure::Function, nchords = 16)
rca(blob::Vector{Blob})
```

画像を検索して、`search` 閾値を満たすピクセルを見つけます。次に、回転弦アルゴリズムを使用して粒子の近似中心を見つけ、中心から等間隔の角度で 2 `nchords` を描画し、`measure` 閾値が満たされなくなるまで続けます。結果として得られる周囲点のセットは `Vector{CartesianIndex}` として保存されます。多くの領域が `search` 閾値を満たす可能性があるため、実際の結果は `Vector{Vector{CartesianIndex}}` です。

注意: 測定の `threshold` は `search` 閾値よりも寛容であるべきです。

例

```
rca(img, p->p>0.9, p->p>0.7) #
bs = blob(img, p->p>0.7)
rca(bs[1])
```
