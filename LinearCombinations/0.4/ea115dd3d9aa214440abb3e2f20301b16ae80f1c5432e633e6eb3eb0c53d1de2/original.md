```
matrixrepr(f, b1::AbstractBasis, b0::AbstractBasis, ::Type{R})) where R
```

Return a matrix representing the linear map `f` with respect to the bases `b0` (source) and `b1` (target). Coefficients have the type `R`.

See also [`matrixrepr!`](@ref).

# Example

```jldoctest
julia> @linear f; f(x) = Linear(uppercase(x) => 1, 'A' => 1)
f (generic function with 2 methods)

julia> matrixrepr(f, Basis('A':'C'), Basis('a':'c'), Int)
3×3 Matrix{Int64}:
 2  1  1
 0  1  0
 0  0  1
```
