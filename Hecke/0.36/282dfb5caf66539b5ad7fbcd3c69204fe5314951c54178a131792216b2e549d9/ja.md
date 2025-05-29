```
quadratic_field(d::IntegerUnion) -> AbsSimpleNumField, AbsSimpleNumFieldElem
```

定義多項式 $x^2 - d$ を持つ体を返します。

# 例

```jldoctest
julia> quadratic_field(5)
(Real quadratic field defined by x^2 - 5, sqrt(5))
```
