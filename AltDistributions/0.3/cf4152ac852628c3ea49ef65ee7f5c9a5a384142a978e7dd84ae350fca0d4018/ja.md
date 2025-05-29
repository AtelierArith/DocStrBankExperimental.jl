```
Fixed(value)
```

値が対数密度計算の目的で「固定」されていることを示すラッパー型。正式には、

```julia
logpdf(d, Fixed(v)) == logpdf(d, v) + C
```

ここで、`C` は `v` のみに依存する定数項です。言い換えれば、

```julia
logpdf(distribution(θ), Fixed(v)) - logpdf(distribution(θ′), Fixed(v))
```

は常に正しく計算されるべきです。値にアクセスするには `get(Fixed(value)` を使用してください。
