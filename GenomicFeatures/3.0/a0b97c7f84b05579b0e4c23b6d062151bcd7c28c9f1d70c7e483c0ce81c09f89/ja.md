```
GenomicInterval{T}(data)
```

返されるデータは、データの型に対して実装された [`Base.convert`](https://docs.julialang.org/en/v1/base/base/#Base.convert) 関数がある場合、GenomicInterval{T} に変換されます。このメソッドは、カスタム型を GenomicInterval{T} に変換するための便利なフックを提供します。
