```
struct WeightedDiracMeasure{T}
    center::Vector{T}
    weight::T
end
```

`center`で中心を持ち、`weight`で重み付けされたディラック測度を表します。
