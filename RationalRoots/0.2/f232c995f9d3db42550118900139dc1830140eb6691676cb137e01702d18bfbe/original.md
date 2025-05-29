```
signedroot([R<:RationalRoot,] x)
```

Return `sign(x)*sqrt(abs(x)) == x/sqrt(abs(x))`. If the first argument is not present, this value is given as a floating point number if `x isa AbstractFloat`, and as a `RationalRoot` if `x isa Union{Integer,Rational}`. With the first argument present, the return type is specified as `RationalRoot` or a specific `RationalRoot{T}`, and for floating point numbers `x` the result will first be rationalized by `Base.rationalize{T}`.

# Examples

```jldoctest
julia> signedroot(3)
+√(3//1)

julia> signedroot(-4.0)
-2.0

julia> signedroot(RationalRoot, 5.2)
+√(26//5)

julia> signedroot(RationalRoot{Int8}, 8)
+√(8//1)
```
