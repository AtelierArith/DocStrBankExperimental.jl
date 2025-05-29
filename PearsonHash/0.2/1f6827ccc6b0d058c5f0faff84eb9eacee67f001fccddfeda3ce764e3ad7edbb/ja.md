```
hash8(data::Vector{UInt8}; seed::UInt8 = zero(UInt8))
hash8(data::AbstractString; seed::UInt8 = zero(UInt8))
```

`data`のためのPearson 8ビットハッシュを計算します（オプションで`seed`を指定できます）。
