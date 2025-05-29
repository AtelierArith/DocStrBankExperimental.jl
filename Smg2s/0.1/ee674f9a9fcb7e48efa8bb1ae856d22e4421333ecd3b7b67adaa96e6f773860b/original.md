```
Spectrum!(spec::AbstractVector{Tv}, f::Function, size::Ti) where {Tv<:Complex, Ti<:Integer}
```

Set the spectrum from user provided function.

## Examples

```jldoctest; setup = :(using SMG2S; using LinearAlgebra)
julia> function f(idx::Integer, size = 10)
           return 10 * cos(((idx-1) / 2) * 2 * π / size) + sin(((idx-1) / 2) * 2 * π / size) * im
       end
f (generic function with 2 methods)

julia> vec=zeros(ComplexF64, 10);

julia> Spectrum!(vec, f, 10);

julia> vec
10-element Vector{ComplexF64}:
                  10.0 + 0.0im
     9.510565162951535 + 0.3090169943749474im
     8.090169943749475 + 0.5877852522924731im
     5.877852522924732 + 0.8090169943749475im
    3.0901699437494745 + 0.9510565162951535im
 6.123233995736766e-16 + 1.0im
   -3.0901699437494736 + 0.9510565162951536im
     -5.87785252292473 + 0.8090169943749475im
    -8.090169943749473 + 0.5877852522924732im
    -9.510565162951535 + 0.3090169943749475im

```
