`N` 個の Chebyshev 多項式の極値を浮動小数点型 `T` で計算し、`domain` で指定された区間にスケーリングします（デフォルトは [1.0,-1.0]）。指定されたドメインにある `N` 個の Chebyshev 極値を型 `T` で含むベクトルを返します。

# シグネチャ

points = chebyshev_extrema(T,N,domain)

# 例

```
julia> using DoubleFloats
julia> points = chebyshev_extrema(Float64,4)
[-1.0
 -5.00000000000000000000000000000002311e-01
  5.00000000000000000000000000000002311e-01
  1.0]

julia> points = chebyshev_extrema(Double64,4,[3.0,-1.0])
[-1.0
 -4.622231866529366e-33
  2.00000000000000000000000000000000462
  3.0]

  julia> points = chebyshev_extrema(BigFloat,4,[3.0,-1.0])
[-1.0
 -1.727233711018888925077270372560079914223200072887256277004740694033718360632485e-77
  2.0
  3.0]
```
