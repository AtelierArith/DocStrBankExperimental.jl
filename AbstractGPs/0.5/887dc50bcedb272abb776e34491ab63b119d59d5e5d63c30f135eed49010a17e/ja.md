```
posterior(fx::FiniteGP{<:PosteriorGP}, y::AbstractVector{<:Real})
```

`f`が`PosteriorGP`であるとき、共分散行列のコレスキー分解を更新し、元の共分散行列から再計算することを避けることによって、`fx.f`の後方分布を構築します。これは`update_chol`機能を使用して行います。

他の側面は通常の後方分布と似ています。
