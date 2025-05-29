```
ReducedLoss(autoencoder)
```

ニューラルネットワークのタイプ[`AutoEncoder`](@ref)に基づいて`ReducedLoss`のインスタンスを作成します。

内部的には次のように行います：

```julia
ReducedLoss(encoder(autoencoder), decoder(autoencoder))
```

したがって、関数[`encoder`](@ref)と[`decoder`](@ref)を呼び出します。
