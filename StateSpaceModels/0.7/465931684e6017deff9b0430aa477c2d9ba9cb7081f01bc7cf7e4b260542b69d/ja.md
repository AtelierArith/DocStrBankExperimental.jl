```
SeasonalNaive(y::Vector{<:Real}, seasoanl::Int)
```

季節的ナイーブモデルで、hステップ先の予測は次のようになります。

$$
y_{T+h|T} = y_{T + h - m(k+1)}
$$

ここで、mは季節的な周期で、kは(h-1)/mの整数部分です。

# 参考文献

  * Hyndman, Rob J., Athanasopoulos, George. "Forecasting: Principles and Practice"
