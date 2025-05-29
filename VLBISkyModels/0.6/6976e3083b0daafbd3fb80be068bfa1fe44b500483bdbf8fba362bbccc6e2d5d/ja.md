```julia
GaussianRing(σ)

```

ガウス環テンプレートを実装します。

## ノート

これは、内部で[`RingTemplate`](@ref)を使用する便利なコンストラクタです。この関数を自分で作成するには、次のようにします。

```julia
RingTemplate(RadialGaussian(σ), AzimuthalUniform())
```

## 引数

  * `σ` : ガウス環の標準偏差
