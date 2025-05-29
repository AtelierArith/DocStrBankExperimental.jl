```
fasthash(v::PackedVector [, h0::UInt]) -> UInt
```

`v` のハッシュを返します。これは、ベクトルの標準的な `hash` よりも高速に計算できる場合があります。この新しいハッシュは、内部ビットサイズ `M` が同じすべての `PackedVector{U,M,T}` に対して一貫性がありますが、異なるビットサイズの `PackedVector` に対しては `hash` や `fasthash` と互換性がない場合があります。ただし、同じ `M` を持つ2つの `PackedVector` に対して `fasthash` を使用すると、符号付きおよび符号なしの要素型 `T` の両方でハッシュ衝突が発生する可能性があります。

関連情報として [`fasthash(::AbstractSmallVector, ::UInt)`](@ref)、`Base.hash` を参照してください。

# 例

```jldoctest
julia> v = PackedVector{UInt64,5,Int8}([1, 5, 6]);

julia> fasthash(v)
0x11e89b9d8f3daac6

julia> fasthash(v) == hash(v)
false

julia> w = PackedVector{UInt128,5,Int8}(v); fasthash(v) == fasthash(w)
true

julia> w = PackedVector{UInt64,4,Int8}(v); fasthash(v) == fasthash(w)
false

julia> w = PackedVector{UInt64,5,UInt8}(v); fasthash(v) == fasthash(w)
true
```
