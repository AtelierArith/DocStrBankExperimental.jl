```
standardize(kr::KRatio, std::KRatio)::KRatio
standardize(kr::KRatios, std::KRatio)::KRatios
standardize(kratios::Union{AbstractVector{KRatio},AbstractVector{<:KRatios}}, stds::AbstractVector{KRatio})
```

If the `std::KRatio` is a suitable match for `kr` then `kr` is restandardized using `std`.  Otherwise, the original `KRatio` or `KRatios` is returned.
