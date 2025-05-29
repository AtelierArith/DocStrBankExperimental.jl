パッケージ: Smoothers

```
sma(x, n, center=false)
```

単純移動平均を使用してデータのベクトルを平滑化します

# 引数

  * `x`: データのベクトル。
  * `n`: 移動平均のサイズ。
  * `center`: テールに欠損値を持つxと同じサイズのベクトルを返します。

# 戻り値

移動平均値のベクトル

# 例

```julia-repl
julia> sma(1:5,3)
3-element Vector{Float64}:
 2.0
 3.0
 4.0

julia> sma(1:5,3,true)
5-element Vector{Union{Missing, Float64}}:
  missing
 2.0
 3.0
 4.0
  missing
```
