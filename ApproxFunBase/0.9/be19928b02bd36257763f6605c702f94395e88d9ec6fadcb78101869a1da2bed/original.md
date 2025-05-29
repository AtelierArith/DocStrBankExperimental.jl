```
PartialInverseOperator(O::Operator, bandwidths = (0, Infinities.ℵ₀))
```

Return an approximate estimate for `inv(O)`, such that `PartialInverseOperator(O) * O` is banded, and is approximately `I` up to a bandwidth that is one less than the sum of the bandwidths of `O` and `PartialInverseOperator(O)`.

!!! note
    Only upper-triangular operators are supported as of now.


# Examples

```jldoctest
julia> C = Conversion(Chebyshev(), Ultraspherical(1));

julia> P = PartialInverseOperator(C); # default bandwidth

julia> P * C
TimesOperator : Chebyshev() → Chebyshev()
 1.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  ⋯
  ⋅   1.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  ⋱
  ⋅    ⋅   1.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  ⋱
  ⋅    ⋅    ⋅   1.0  0.0  0.0  0.0  0.0  0.0  0.0  ⋱
  ⋅    ⋅    ⋅    ⋅   1.0  0.0  0.0  0.0  0.0  0.0  ⋱
  ⋅    ⋅    ⋅    ⋅    ⋅   1.0  0.0  0.0  0.0  0.0  ⋱
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅   1.0  0.0  0.0  0.0  ⋱
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅   1.0  0.0  0.0  ⋱
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅   1.0  0.0  ⋱
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅   1.0  ⋱
  ⋮    ⋱    ⋱    ⋱    ⋱    ⋱    ⋱    ⋱    ⋱    ⋱   ⋱

julia> P = PartialInverseOperator(C, (0, 4)); # specify an upper bandwidth

julia> P * C
TimesOperator : Chebyshev() → Chebyshev()
 1.0  0.0  0.0  0.0  0.0  0.0  -0.5    ⋅     ⋅     ⋅   ⋅
  ⋅   1.0  0.0  0.0  0.0  0.0   0.0  -1.0    ⋅     ⋅   ⋅
  ⋅    ⋅   1.0  0.0  0.0  0.0   0.0   0.0  -1.0    ⋅   ⋅
  ⋅    ⋅    ⋅   1.0  0.0  0.0   0.0   0.0   0.0  -1.0  ⋅
  ⋅    ⋅    ⋅    ⋅   1.0  0.0   0.0   0.0   0.0   0.0  ⋱
  ⋅    ⋅    ⋅    ⋅    ⋅   1.0   0.0   0.0   0.0   0.0  ⋱
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    1.0   0.0   0.0   0.0  ⋱
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅     ⋅    1.0   0.0   0.0  ⋱
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅     ⋅     ⋅    1.0   0.0  ⋱
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅     ⋅     ⋅     ⋅    1.0  ⋱
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅     ⋅     ⋅     ⋅     ⋅   ⋱
```
