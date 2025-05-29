```
GATv2Conv(in => out, σ=identity; heads=1, concat=true,
          init=glorot_uniform, negative_slope=0.2)
```

グラフ注意層 v2。

# 引数

  * `in`: 入力特徴の次元。
  * `out`: 出力特徴の次元。
  * `σ`: 活性化関数。
  * `heads`: 注意ヘッドの数。
  * `concat`: 層の出力を連結するかどうか。連結しない場合、層の出力は平均化される。
  * `negative_slope::Real`: キーワード引数、LeakyReLUのパラメータ。

# 例

```jldoctest
julia> GATv2Conv(1024=>256, relu)
GATv2Conv(1024=>256, relu, heads=1, concat=true, LeakyReLU(λ=0.2))

julia> GATv2Conv(1024=>256, relu, heads=4)
GATv2Conv(1024=>1024, relu, heads=4, concat=true, LeakyReLU(λ=0.2))

julia> GATv2Conv(1024=>256, relu, heads=4, concat=false)
GATv2Conv(1024=>1024, relu, heads=4, concat=false, LeakyReLU(λ=0.2))

julia> GATv2Conv(1024=>256, relu, negative_slope=0.1f0)
GATv2Conv(1024=>256, relu, heads=1, concat=true, LeakyReLU(λ=0.1))
```

静的グラフでの層のトレーニングについては、[`WithGraph`](@ref)を参照してください。
