```
PermuteDims(perm)
```

`ArrayItem`の次元を並べ替えます。`perm`は、並べ替えを指定するベクトルまたはタプルで、長さは`ArrayItem`のデータの次元数と一致する必要があります。

並べ替えベクトル`perm`の例については、`permutedims`のドキュメントを参照してください。

`apply!`をサポートしています。

## 例

3つのカラーチャンネルを持つ画像の前処理。

{cell=PermuteDims}

```julia
using DataAugmentation, Images
image = Image(rand(RGB, 20, 20))

# 画像をテンソルに変換し、次元2と1を並べ替えます
# HWC（高さ、幅、チャンネル）配列をWHC（幅、高さ、チャンネル）に変換します
tfms = ImageToTensor() |> PermuteDims(2, 1, 3)
apply(tfms, image)
```
