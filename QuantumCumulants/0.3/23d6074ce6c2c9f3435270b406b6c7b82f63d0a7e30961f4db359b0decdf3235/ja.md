```
average(::QNumber)
average(::QNumber,order)
```

演算子の平均を計算します。`order`が指定されている場合、その順までの[`cumulant_expansion`](@ref)が即座に計算されます。
