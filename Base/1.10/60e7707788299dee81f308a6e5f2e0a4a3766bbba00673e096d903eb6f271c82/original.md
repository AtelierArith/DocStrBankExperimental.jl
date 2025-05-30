```
^(x, y)
```

Exponentiation operator. If `x` is a matrix, computes matrix exponentiation.

If `y` is an `Int` literal (e.g. `2` in `x^2` or `-3` in `x^-3`), the Julia code `x^y` is transformed by the compiler to `Base.literal_pow(^, x, Val(y))`, to enable compile-time specialization on the value of the exponent. (As a default fallback we have `Base.literal_pow(^, x, Val(y)) = ^(x,y)`, where usually `^ == Base.^` unless `^` has been defined in the calling namespace.) If `y` is a negative integer literal, then `Base.literal_pow` transforms the operation to `inv(x)^-y` by default, where `-y` is positive.

# Examples

```jldoctest
julia> 3^5
243

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> A^3
2×2 Matrix{Int64}:
 37   54
 81  118
```
