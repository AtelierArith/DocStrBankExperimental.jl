```
kurtosis(::ContinuousHistogram [, excess = true ])
```

[Pearson（`excess`）尖度](https://en.wikipedia.org/wiki/Kurtosis?oldformat=true#Pearson_moments) of a [`ContinuousHistogram`](@ref).

!!! note
    比較のために、この `kurtosis` 定義は、`excess == true` の場合、ガウス分布に適用すると `0` になります。`excess == false` の場合、ガウスの尖度は 3 です。

