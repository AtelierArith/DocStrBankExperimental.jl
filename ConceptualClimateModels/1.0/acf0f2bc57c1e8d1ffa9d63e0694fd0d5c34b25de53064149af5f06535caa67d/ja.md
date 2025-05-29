```
plausible_limits(ds::DynamicalSystem [, idxs])
```

`ds`の各動的状態変数に対する制限（最小値、最大値）のベクトルを返します。オプションで、`ds`の参照MTKモデルに存在する記号変数の`Symbol`のベクトルとして使用する変数の`idxs`を提供できます。

[`plausible_grid`](@ref)や[`plausible_ic_sampler`](@ref)も参照してください。
