```
forecastvar!(out::AbstractArray{T,3}, irfs::AbstractArray{T,3})
```

`irfs`で指定された直交インパルス応答係数に基づいて、各ホライズンにわたる予測誤差の分散を計算し、その結果を配列`out`に格納します。計算されるホライズンの数は`irfs`の第二次元によって決まり、`out`は`irfs`と同じサイズである必要があります。詳細は[`forecastvar`](@ref)を参照してください。
