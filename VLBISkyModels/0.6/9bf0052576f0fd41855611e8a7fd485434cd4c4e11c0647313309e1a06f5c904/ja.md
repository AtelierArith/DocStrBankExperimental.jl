```
ContinuousImage{A<:IntensityMap, P} <: AbstractModel
ContinuousImage(img::Intensitymap, kernel)
```

VLBISkyModelsの基本的な連続画像モデルです。これは、画像としてIntensityMapスタイルのオブジェクトと、任意の画像および可視性位置で画像を評価できる画像カーネルまたはパルスを期待します。画像モデルは次のようになります。

```
I(x,y) = ∑ᵢ Iᵢⱼ κ(x-xᵢ, y-yᵢ)
```

ここで、`Iᵢⱼ`は画像`img`のフラックス密度であり、κは`kernel`の強度関数です。
