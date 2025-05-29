```
RandPermGibbs(unislice)
```

ランダムな順序で座標ごとのギブスサンプリング戦略。この戦略は、`unislice`を座標ごとに適用します。

# 引数

  * `unislice::Union{<:AbstractUnivariateSliceSampling,<:AbstractVector{<:AbstractUnivariateSliceSampling}}`: 単一またはベクトルの一変量スライスサンプリングアルゴリズム。

`unislice`がサンプラーのベクトルである場合、各スライスサンプラーはターゲットの事後分布の対応する座標に適用されます。その場合、`length(unislice)`は事後分布の次元数と一致する必要があります。
