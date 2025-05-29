```
autocorrelation(x::Array, k::Int; flag::Bool=false)
```

時系列の自己相関関数を計算します。

# 引数

  * `x::Array`: 時系列。
  * `k::Int`: 自己相関のラグ。

# 出力

  * `acf::Array`: 自己相関関数。

# オプション引数

  * `flag::Bool`: trueの場合、自己相関関数が表示されます。

# 例

```julia
julia> autocorrelation(randn(100), 10)
```
