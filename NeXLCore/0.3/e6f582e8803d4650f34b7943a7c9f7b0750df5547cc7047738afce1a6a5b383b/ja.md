```
standardize(kr::KRatio, std::KRatio)::KRatio
standardize(kr::KRatios, std::KRatio)::KRatios
standardize(kratios::Union{AbstractVector{KRatio},AbstractVector{<:KRatios}}, stds::AbstractVector{KRatio})
```

もし `std::KRatio` が `kr` に適した一致であれば、`kr` は `std` を使用して再標準化されます。そうでなければ、元の `KRatio` または `KRatios` が返されます。
