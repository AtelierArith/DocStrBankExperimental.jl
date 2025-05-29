# 拡張ヘルプ

```
sample(B::Ball2, [nsamples]::Int;
       [rng]::AbstractRNG=GLOBAL_RNG,
       [seed]::Union{Int, Nothing}=nothing)
```

### アルゴリズム

`B` 内での一様分布によるランダムサンプリングは、正規化されたガウスのムラー法を使用して計算されます。この方法は `Distributions` パッケージを必要とします。実装の詳細については [`_sample_unit_nball_muller!`](@ref) を参照してください。
