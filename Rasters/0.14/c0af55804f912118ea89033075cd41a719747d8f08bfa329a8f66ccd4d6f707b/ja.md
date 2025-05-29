```
Mapped <: AbstractProjected

Mapped(order, span, sampling, crs, mappedcrs)
Mapped(; order=AutoOrder(), span=AutoSpan(), sampling=AutoSampling(), crs=nothing, mappedcrs)
```

[`AbstractSampled`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Lookups.AbstractSampled) `Lookup`で、次元インデックスが別の投影にマッピングされており、通常は緯度/経度または`EPSG(4326)`です。`Mapped`は、netcdfファイルで一般的に使用される次元形式に一致します。

フィールドと動作は、`crs`および`mappedcrs`フィールドの追加を除いて、[`Sampled`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Lookups.Sampled)と同一です。

マッピングされた次元インデックスは、[`Sampled`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Lookups.Sampled)と同様に使用されますが、別の形式で保存するために、基になる`crs`を使用して変換される場合があります。
