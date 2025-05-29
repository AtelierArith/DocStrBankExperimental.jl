```
bits(x::Real)
```

`x`のビットに対する不変のビューを`Bool`のベクトルとして作成します。これは`BitVector`に似ています。`x`が`BigInt`の場合、ベクトルの長さは[`Bits.INF`](@ref)です。現在、ベクトルにインデックスを付ける際に境界チェックは行われません。

# 例

```jldoctest
julia> v = bits(Int16(2^8+2^4+2+1))
<00000001 00010011>

julia> permutedims([v[i] for i in 8:-1:1])
1×8 Array{Bool,2}:
 false  false  false  true  false  false  true  true

julia> bits(true)
<1>

julia> bits(big(2)^63)
<...0 10000000 00000000 00000000 00000000 00000000 00000000 00000000 00000000>

julia> bits(Float32(-7))
<1|10000001|1100000 00000000 00000000>

julia> ans[1:23] # 特定の長さのビットベクトルを作成
<1100000 00000000 00000000>
```
