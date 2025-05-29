```
AdjustBrightness(δ = 0.2)
AdjustBrightness(distribution)
```

画像の明るさを `f ∈ [1-δ, 1+δ]` から均等に選ばれた因子で調整し、各色チャネルに `f` を掛けます。

因子が選択される任意の `Distributions.Sampleable` を渡すこともできます。

ピクセルは `[0,1]` に制限されますが、`clamp=false` が渡された場合は制限されません。

## 例

```julia
using DataAugmentation, TestImages

item = Image(testimage("lighthouse"))
tfm = AdjustBrightness(0.2)
titems = [apply(tfm, item) for _ in 1:8]
showgrid(titems; ncol = 4, npad = 16)
```
