```
ThreefryNoise{N,T,R} <: AbstractNoise{NTuple{N,T}}
```

ThreefryファミリーのCBRNGに基づくノイズ関数です。

これは[`Threefry2x`](@ref)および[`Threefry4x`](@ref)からのラッパーであり、[`Random123`](@ref)のもので、イミュータビリティを保証します。

## 例

```jldoctest
julia> tf = Threefry2x()
Threefry2x{UInt64, 20}(0x2e5a37d3f55d93a2, 0xb2eabf28f8527ba2, 0x7c000c9ca153ea29, 0xe5cc75bfdad28187, 0x0000000000000000, 0x0000000000000000, 0)

julia> tfn = ThreefryNoise(tf)
ThreefryNoise{2, UInt64, 20}((0x7c000c9ca153ea29, 0xe5cc75bfdad28187))

julia> noise(1, tfn)
(0xfdef457ec97615d8, 0x9813921752436c1c)
```
