```julia
struct BicubicPulse{T} <: VLBISkyModels.Pulse
```

```
BicubicPulse(b = 0.5)
```

画像用のバイキュービックパルス。このパルスは平坦なスペクトルを持つ傾向がありますが、`b`のほとんどの値に対して画像に負の強度を生成する可能性があります。これは[`Broderick et al. 2020`](https://iopscience.iop.org/article/10.3847/1538-4357/ab9c1f)で使用されているパルスです。
