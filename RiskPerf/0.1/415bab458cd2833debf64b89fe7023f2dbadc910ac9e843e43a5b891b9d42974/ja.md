```
log_returns(prices::Vector; drop_first=false, first_value=NaN)
```

提供された `N` の価格の時系列に基づいて、対数リターン系列を計算します。提供された価格系列は、例えば時間ごとや日ごとのデータのように、定期的に間隔を空けている必要があります。

# 引数

  * `prices`: 価格のベクター。
  * `drop_first`: 最初のリターンを削除するかどうかを示すブール値（デフォルト=false）。
  * `first_value`: `drop_first=false` の場合に最初のリターンに使用される値。

# 公式

$$
r_t = \log\left(\dfrac{P_t}{P_{t-1}}\right)
$$

ここで、$r_t$ は時刻 $t$ のリターン、$P_t$ は時刻 $t$ の価格、$P_{t-1}$ は時刻 $t-1$ の価格です。

# 例

```jldoctest
julia> using RiskPerf

julia> prices = [100.0, 101.0, 100.5, 99.8, 101.3]
5-element Vector{Float64}:
 100.0
 101.0
 100.5
  99.8
 101.3

julia> log_returns(prices)
5-element Vector{Float64}:
 NaN
   0.009950330853168092
  -0.004962789342129014
  -0.006989544181712186
   0.014918227937219366

julia> log_returns(prices; drop_first=true)
4-element Vector{Float64}:
  0.009950330853168092
 -0.004962789342129014
 -0.006989544181712186
  0.014918227937219366
```
