```
noise_warp(img, noise_source::AbstractSampler; squared = true, variance = 0.1, crop = true)
```

`noise_warp` は `img` と `CoherentNoise.jl` から構築された `noise_source` の両方を受け取り、変形された画像を返します。原理は簡単です：

  * `noise_source` を使用して2つのノイズ行列が生成されます。
  * これらの行列は、値を0の周りに中心化し、`variance * size` でスケーリングすることによってベクトル場に変換されます。
  * ベクトル場は、x/y座標場におけるピクセルの変位に対応します。
  * `ImageTransformations` は変換を適用し、画像を適応的に変形します。
  * `crop` が true の場合、画像は `NaN` 値が含まれないようにトリミングされます。
