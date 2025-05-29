```
a = nomissing(da)
```

型 `Array{Union{T,Missing},N}` の配列 `da` の値を、同じ要素型の通常の Julia 配列 `a` として返します。配列に少なくとも1つの欠損値が含まれている場合は、エラーが発生します。
