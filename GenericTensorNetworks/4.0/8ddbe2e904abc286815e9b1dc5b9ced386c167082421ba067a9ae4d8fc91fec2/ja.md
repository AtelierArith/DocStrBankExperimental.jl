```
TruncatedPoly{K,T,TO} <: Number
TruncatedPoly(coeffs::Tuple, maxorder)
```

多項式は最大 `K` 次まで切り捨てられます。`T` は係数の型で、`TO` は次数の型です。

## フィールド

  * `coeffs` は多項式の最大-K 係数です。`GenericTensorNetworks` では、解のカウントまたは列挙である可能性があります。
  * `maxorder` は多項式の次数です。

## 例

```jldoctest; setup=(using GenericTensorNetworks)
julia> TruncatedPoly((1,2,3), 6)
x⁴ + 2*x⁵ + 3*x⁶

julia> TruncatedPoly((1,2,3), 6) * TruncatedPoly((5,2,1), 3)
20*x⁷ + 8*x⁸ + 3*x⁹

julia> TruncatedPoly((1,2,3), 6) + TruncatedPoly((5,2,1), 3)
x⁴ + 2*x⁵ + 3*x⁶
```
