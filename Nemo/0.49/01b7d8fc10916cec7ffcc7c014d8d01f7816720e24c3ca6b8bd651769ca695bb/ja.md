```
crt(r1::ZZRingElem, m1::ZZRingElem, r2::ZZRingElem, m2::ZZRingElem, signed=false; check::Bool=true)
crt(r1::ZZRingElem, m1::ZZRingElem, r2::Union{Int, UInt}, m2::Union{Int, UInt}, signed=false; check::Bool=true)
crt(r::Vector{ZZRingElem}, m::Vector{ZZRingElem}, signed=false; check::Bool=true)
crt_with_lcm(r1::ZZRingElem, m1::ZZRingElem, r2::ZZRingElem, m2::ZZRingElem, signed=false; check::Bool=true)
crt_with_lcm(r1::ZZRingElem, m1::ZZRingElem, r2::Union{Int, UInt}, m2::Union{Int, UInt}, signed=false; check::Bool=true)
crt_with_lcm(r::Vector{ZZRingElem}, m::Vector{ZZRingElem}, signed=false; check::Bool=true)
```

AbstractAlgebra `crt` インターフェースに従い、次のオプションがあります。`signed = true` の場合、解は範囲 $(-m/2, m/2]$ にあり、そうでない場合は範囲 $[0,m)$ にあります。ここで、$m$ は剰余の最小公倍数です。

# 例

```jldoctest
julia> crt(ZZ(5), ZZ(13), ZZ(7), ZZ(37), true)
44

julia> crt(ZZ(5), ZZ(13), 7, 37, true)
44
```
