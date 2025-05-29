```
Normalize(means, stds)
```

`AbstractArrayItem{N}`の最後の次元を正規化します。

`apply!`をサポートしています。

## 例

3つのカラーチャンネルを持つ3D画像の前処理。

{cell=Normalize}

```julia
using DataAugmentation, Images
image = Image(rand(RGB, 20, 20, 20))
tfms = ImageToTensor() |> Normalize((0.1, -0.2, -0.1), (1,1,1.))
apply(tfms, image)
```
