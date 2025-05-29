```
fasthash(v::AbstractFixedVector [, h0::UInt]) -> UInt
```

`v` のハッシュを返します。これはベクトルの標準の `hash` よりも高速に計算できる場合があります。この新しいハッシュは、同じ要素型のすべての `AbstractFixedVector` に対して一貫性がありますが、異なる要素型を持つ `AbstractFixedVector` の `hash` や `fasthash` とは互換性がない場合があります。

現在、`fasthash` は、`v` の要素型が最大 32 ビットのビット整数型、`Bool` または `Char` の場合にのみ `hash` と異なります。

`Base.hash` も参照してください。
