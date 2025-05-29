```
sample([rng::AbstractRNG], model::StateSpaceModel, T::Integer; kwargs...)
```

状態空間モデルから長さ `T` の軌道をシミュレートします。

初期状態 `x0`、潜在状態のベクトル `xs`、観測のベクトル `ys` からなるタプル `(x0, xs, ys)` を返します。
