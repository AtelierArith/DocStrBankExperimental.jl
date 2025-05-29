```
PhiloxNoise{N,T,R,K} <: AbstractNoise{NTuple{N,T}}
```

PhiloxファミリーのCBRNGに基づくノイズ関数です。

これは[`Philox2x`](@ref)および[`Philox4x`](@ref)からのラッパーであり、[`Random123`](@ref)のもので、イミュータビリティを保証します。

## 例

```jldoctest
julia> ph = Philox2x()
Philox2x{UInt64, 10}(0x4d6efe7f510f82b6, 0xd79c03fecfefaf49, 0x429f6e3e1bf363f1, 0x0000000000000000, 0x0000000000000000, 0)

julia> phn = PhiloxNoise(ph)
PhiloxNoise{2, UInt64, 10, Tuple{UInt64}}((0x429f6e3e1bf363f1,))

julia> noise(1, phn)
(0x968ebada8eb2b209, 0xd0669e24b96570df)
```
