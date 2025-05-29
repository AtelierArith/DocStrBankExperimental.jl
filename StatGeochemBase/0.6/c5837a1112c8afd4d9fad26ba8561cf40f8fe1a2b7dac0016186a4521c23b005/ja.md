```julia
renormalize!(A::AbstractArray; dim, total=1.0)
```

配列 `A` をその合計が `total` になるようにインプレースで正規化します。オプションで、正規化する次元 `dim` を指定できます。
