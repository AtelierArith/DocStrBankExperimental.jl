```
crt(r1::ZZRingElem, m1::ZZRingElem, r2::ZZRingElem, m2::ZZRingElem, signed=false; check::Bool=true)
crt(r1::ZZRingElem, m1::ZZRingElem, r2::Union{Int, UInt}, m2::Union{Int, UInt}, signed=false; check::Bool=true)
crt(r::Vector{ZZRingElem}, m::Vector{ZZRingElem}, signed=false; check::Bool=true)
crt_with_lcm(r1::ZZRingElem, m1::ZZRingElem, r2::ZZRingElem, m2::ZZRingElem, signed=false; check::Bool=true)
crt_with_lcm(r1::ZZRingElem, m1::ZZRingElem, r2::Union{Int, UInt}, m2::Union{Int, UInt}, signed=false; check::Bool=true)
crt_with_lcm(r::Vector{ZZRingElem}, m::Vector{ZZRingElem}, signed=false; check::Bool=true)
```

As per the AbstractAlgebra `crt` interface, with the following option. If `signed = true`, the solution is the range $(-m/2, m/2]$, otherwise it is in the range $[0,m)$, where $m$ is the least common multiple of the moduli.

# Examples

```jldoctest
julia> crt(ZZ(5), ZZ(13), ZZ(7), ZZ(37), true)
44

julia> crt(ZZ(5), ZZ(13), 7, 37, true)
44
```
