```
AdjustContrast(factor = 0.2)
AdjustContrast(distribution)
```

画像のコントラストを `f ∈ [1-δ, 1+δ]` から均等に選ばれた因子で調整します。

ピクセル `c` は `c + μ*(1-f)` に変換され、ここで `μ` は画像の平均色です。

因子が選択される任意の `Distributions.Sampleable` を渡すこともできます。

ピクセルは `[0,1]` に制限されますが、`clamp=false` が渡された場合は制限されません。

## 例

```julia
using DataAugmentation, TestImages

item = Image(testimage("lighthouse"))
tfm = AdjustContrast(0.2)
titems = [apply(tfm, item) for _ in 1:8]
showgrid(titems; ncol = 4, npad = 16)
```
