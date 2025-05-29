```
make_random_psd_matrix_from_wishart(
    num_assets::Integer,
    rng::Union{MersenneTwister,StableRNG} = MersenneTwister(1),
)
```

逆ウィシャート分布からランダムなpsd行列を作成します。

### 入力

  * `num_assets` - 資産の数。
  * `rng` - RNGに使用されるRandom.MersenneTwisterまたはStableRNGs.Stable。

### 返り値

  * `Hermitian`
