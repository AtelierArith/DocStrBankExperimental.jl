```
externalsampler(sampler::AbstractSampler; adtype=AutoForwardDiff(), unconstrained=true)
```

サンプラーをラップして、推論アルゴリズムとして使用できるようにします。

# 引数

  * `sampler::AbstractSampler`: ラップするサンプラー。

# キーワード引数

  * `adtype::ADTypes.AbstractADType=ADTypes.AutoForwardDiff()`: 使用する自動微分 (AD) バックエンド。
  * `unconstrained::Bool=true`: サンプラーが制約のない空間を必要とするかどうか。
