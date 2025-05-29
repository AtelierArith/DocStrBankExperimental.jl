```
fasthash(v::AbstractSmallVector [, h0::UInt]) -> UInt
```

`v` のハッシュを返します。これはベクトルの標準的な `hash` よりも高速に計算できる場合があります。この新しいハッシュは、同じ要素型のすべての `AbstractSmallVector` に対して一貫性がありますが、異なる要素型の `AbstractSmallVector` に対しては `hash` や `fasthash` と互換性がない場合があります。

現在、`fasthash` は、`v` の要素型が最大32ビットのビット整数型、`Bool` または `Char` の場合にのみ `hash` と異なります。

関連情報として [`fasthash(::PackedVector, ::UInt)`](@ref)、`Base.hash` を参照してください。

# 例

```jldoctest
julia> v = SmallVector{8,Int8}([1, 5, 6]);

julia> fasthash(v)
0x6466067ab41d0916

julia> fasthash(v) == hash(v)
false

julia> w = SmallVector{16,Int8}(v); fasthash(v) == fasthash(w)
true

julia> w = SmallVector{8,Int16}(v); fasthash(v) == fasthash(w)
false
```
