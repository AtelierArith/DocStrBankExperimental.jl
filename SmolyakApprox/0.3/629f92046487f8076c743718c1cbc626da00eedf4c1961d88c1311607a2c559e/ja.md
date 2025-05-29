`N` 個の浮動小数点型 `T` の均等に間隔を空けた点を [1.0,-1.0] 上で計算し、指定された `domain` の範囲にスケーリングします（デフォルトは [1.0,-1.0]）。指定されたドメイン上に位置する `N` 点を含むベクターを返します。

# シグネチャ

points = clenshaw*curtis*equidistant(T,N,domain)

# 例

```
julia> using DoubleFloats
julia> points = clenshaw_curtis_equidistant(Double64,4)
[-1.0
 -0.33333333333333337
  0.33333333333333337
  1.0]

julia> points = clenshaw_curtis_equidistant(Double64,4,[3.0,-1.0])
[-1.0
  0.33333333333333326
  1.6666666666666667
  3.0]

  julia> points = clenshaw_curtis_equidistant(BigFloat,4,[3.0,-1.0])
[-1.0
  0.3333333333333332593184650249895639717578887939453125
  1.6666666666666667406815349750104360282421112060546875
  3.0]
```
