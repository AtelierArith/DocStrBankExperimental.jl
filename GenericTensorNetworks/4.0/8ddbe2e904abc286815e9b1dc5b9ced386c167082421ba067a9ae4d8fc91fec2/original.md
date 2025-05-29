```
TruncatedPoly{K,T,TO} <: Number
TruncatedPoly(coeffs::Tuple, maxorder)
```

Polynomial truncated to largest `K` orders. `T` is the coefficients type and `TO` is the orders type.

## Fields

  * `coeffs` is the largest-K coefficients of a polynomial. In `GenericTensorNetworks`, it can be the counting or enumeration of solutions.
  * `maxorder` is the order of a polynomial.

## Examples

```jldoctest; setup=(using GenericTensorNetworks)
julia> TruncatedPoly((1,2,3), 6)
x⁴ + 2*x⁵ + 3*x⁶

julia> TruncatedPoly((1,2,3), 6) * TruncatedPoly((5,2,1), 3)
20*x⁷ + 8*x⁸ + 3*x⁹

julia> TruncatedPoly((1,2,3), 6) + TruncatedPoly((5,2,1), 3)
x⁴ + 2*x⁵ + 3*x⁶
```
