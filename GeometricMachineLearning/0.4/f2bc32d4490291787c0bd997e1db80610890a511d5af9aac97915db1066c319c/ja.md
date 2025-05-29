```
ResNet(dim, n_blocks, activation)
```

`ResNet`のインスタンスを作成します。

ResNetは、次の形式のマッピングを実現するニューラルネットワークです：

$$
    x = \mathcal{NN}(x) + x,
$$

したがって、入力は出力に再び加算されます（いわゆる加算接続）。`GeometricMachineLearning`で使用する特定のResNetは、一連の単純な[`ResNetLayer`](@ref)で構成されています。

# コンストラクタ

`ResNet`は次のコンストラクタで呼び出すこともできます：

```julia
ResNet(dl, n_blocks)
```

ここで、`dl`は`DataLoader`のインスタンスです。

例については[`iterate`](@ref)を参照してください。
