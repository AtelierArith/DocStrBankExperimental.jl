```
heat_index(Tair::T, RH::T) where {T<:Real}
```

気温 `Tair`（摂氏）と相対湿度 `RH`（パーセント）を考慮して、熱指数を計算します。

# 引数

  * `Tair::T`: 摂氏の気温。
  * `RH::T`: パーセントの相対湿度。

# 戻り値

  * `HI::Float64`: 摂氏の熱指数。

# 例

```julia-repl
julia> heat_index(30, 50)
31.049081444444305
```

# 参考文献

1. Steadman, R. G. “The Assessment of Sultriness. Part I: A Temperature-Humidity Index Based on Human Physiology and Clothing Science.” Journal of Applied Meteorology 18, no. 7 (July 1979): 861–73. https://doi.org/10.1175/1520-0450(1979)018<0861:TAOSPI>2.0.CO;2.
2. Steadman, Robert G. “A Universal Scale of Apparent Temperature.” Journal of Climate and Applied Meteorology 23, no. 12 (December 1984): 1674–87. https://doi.org/10.1175/1520-0450(1984)023<1674:AUSOAT>2.0.CO;2.
3. Rothfusz, Lans P. “The Heat Index ‘Equation’ (or, More Than You Ever Wanted to Know About Heat Index),” 1990.
4. Anderson, G. Brooke, Michelle L. Bell, and Roger D. Peng. “Methods to Calculate the Heat Index as an Exposure Metric in Environmental Health Research.” Environmental Health Perspectives 121, no. 10 (October 2013): 1111–19. https://doi.org/10.1289/ehp.1206273.
