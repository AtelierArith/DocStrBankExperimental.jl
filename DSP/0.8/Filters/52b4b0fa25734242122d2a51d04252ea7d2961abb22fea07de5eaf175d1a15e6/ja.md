```
resample(x::AbstractArray, rate::Real, h::Vector = resample_filter(rate); dims)
resample(x::AbstractArray, rate::AbstractFloat, h::Vector, Nϕ=32; dims)
```

配列 `x` を次元 `dims` に沿って再サンプリングします。`rate` が `AbstractFloat` の場合、`FIRArbitrary` を構築するために使用される位相の数 `Nϕ` をオプション引数として指定できます。デフォルトは 32 です。
