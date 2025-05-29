```
PartialInverseOperator(O::Operator, bandwidths = (0, Infinities.ℵ₀))
```

`inv(O)`の近似推定値を返します。ここで、`PartialInverseOperator(O) * O`はバンド付きであり、`O`と`PartialInverseOperator(O)`のバンド幅の合計より1少ないバンド幅までの`I`に近似されます。

!!! note
    現在、上三角行列の演算子のみがサポートされています。


# 例

```jldoctest
julia> C = Conversion(Chebyshev(), Ultraspherical(1));

julia> P = PartialInverseOperator(C); # デフォルトのバンド幅

julia> P * C
TimesOperator : Chebyshev() → Chebyshev()
 1.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  ⋯
  ⋅   1.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  ⋱
  ⋅    ⋅   1.0  0.0  0.0  0.0  0.0  0.0  0.0  ⋱
  ⋅    ⋅    ⋅   1.0  0.0  0.0  0.0  0.0  0.0  ⋱
  ⋅    ⋅    ⋅    ⋅   1.0  0.0  0.0  0.0  0.0  0.0  ⋱
  ⋅    ⋅    ⋅    ⋅    ⋅   1.0  0.0  0.0  0.0  0.0  ⋱
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅   1.0  0.0  0.0  0.0  ⋱
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅   1.0  0.0  0.0  ⋱
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅   1.0  0.0  ⋱
  ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅    ⋅   1.0  ⋱
  ⋮    ⋱    ⋱    ⋱    ⋱    ⋱    ⋱    ⋱    ⋱    ⋱   ⋱

julia> P = PartialInverseOperator(C, (0, 4)); # 上バンド幅を指定

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
