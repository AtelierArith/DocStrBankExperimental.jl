```julia
SlashedGaussianRing(σ, s)

```

スラッシュガウスリングテンプレートを実装します。これはコサインを使用してスラッシュを実装し、北の東0度の明るさ位置角を持ちます。

## 引数

  * `σ` : ガウスリングの標準偏差
  * `s` : スラッシュ振幅。0はスラッシュなし、1は最大です。

## 注意事項

これは、内部で[`RingTemplate`](@ref)を使用する便利なコンストラクタです。この関数を自分で作成するには、次のようにします。

```julia
RingTemplate(RadialGaussian(σ), AzimuthalCosine((s,), (zero(s),)))
```
