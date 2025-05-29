```
fit_linear_data(x_data, y_data)
```

2つのデータベクトルを線形モデルにフィットさせ、その傾きと切片を返します。傾きと切片はどちらも`measurement`型であり、不確かさはフィッティングの標準誤差になります。

!!! note
    入力データが`measurement`の場合、`y_data`の不確かさは各データポイントの重要性を重み付けするために使用されます。[アレクサンダー・エイトキン](https://en.wikipedia.org/wiki/Alexander_Aitken)は、分散の逆数に従って重み付けすることが[最良線形不偏推定量 (BLUE)](https://en.wikipedia.org/wiki/Gauss%E2%80%93Markov_theorem)であることを示しました。線形回帰における重み付き最小二乗法については[こちら](https://en.wikipedia.org/wiki/Weighted_least_squares)をお読みください。

