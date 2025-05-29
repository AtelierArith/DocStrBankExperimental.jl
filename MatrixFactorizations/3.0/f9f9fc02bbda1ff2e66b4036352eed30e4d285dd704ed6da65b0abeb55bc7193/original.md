```
ul!(A, pivot=Val(true); check = true) -> UL
```

`ul!` is the same as [`ul`](@ref), but saves space by overwriting the input `A`, instead of creating a copy. An [`InexactError`](@ref) exception is thrown if the factorization produces a number not representable by the element type of `A`, e.g. for integer types.

# Examples

```jldoctest
julia> A = [4. 3.; 6. 3.]
2×2 Array{Float64,2}:
 4.0  3.0
 6.0  3.0

julia> F = ul!(A)
UL{Float64,Array{Float64,2},Vector{Int}}
L factor:
2×2 Array{Float64,2}:
 1.0       0.0
 0.666667  1.0
U factor:
2×2 Array{Float64,2}:
 6.0  3.0
 0.0  1.0

julia> iA = [4 3; 6 3]
2×2 Array{Int64,2}:
 4  3
 6  3

julia> ul!(iA)
ERROR: InexactError: Int64(0.6666666666666666)
Stacktrace:
[...]
```
