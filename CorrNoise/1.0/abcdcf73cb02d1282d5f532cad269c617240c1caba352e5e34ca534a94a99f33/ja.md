```
GaussRNG(flatrng::AbstractRNG)
GaussRNG(seed=0)
```

ガウス乱数生成器を初期化します。パラメータ `flatrng` は一様乱数生成器でなければなりません。`seed` が使用される場合、`MersenneTwister` 乱数生成器が使用されます。
