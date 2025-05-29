```
support(basis::BSplineBasis) -> a, b
```

Bスプライン基底が定義されている区間 $[a,b]$ を返します。すなわち、`a` は最初のブレークポイントで、`b` は `basis` の最後のブレークポイントです。

# 例

```jldoctest
julia> support(BSplineBasis(3, 0:5))
(0, 5)

julia> support(BSplineBasis(4, [1.0, 1.5, 2.5, 4.0]))
(1.0, 4.0)
```
