```
SparseUnidimensionalInterpolator{T=eltype(ker)}(ker, d, pos, grd)
```

は、カーネル `ker` を用いて配列の `d` 次元を位置 `pos` で補間する線形マッピングを生成します。補間の次元 `d` に沿った入力配列のグリッド座標は `grd` であると仮定します。引数 `pos` は位置のベクトルであり、引数 `grd` は範囲または補間の次元の長さである可能性があります。オプションのパラメータ `T` は演算子の係数の浮動小数点型です。

この種の補間器は、事前に計算された補間係数を用いた分離可能な多次元補間に適しています。事前に計算された係数は、演算子が複数回適用される場合（例えば反復法において）に特に興味深いです。それ以外の場合、係数を*その場で*計算する分離可能な演算子の方が好ましいかもしれません。

`SparseUnidimensionalInterpolator` のインスタンスの組み合わせを構築することで、分離可能な多次元補間を実現できます。例えば：

```
using LinearInterpolators
ker = CatmullRomSpline()
n1, n2 = 70, 50
x1 = linspace(1, 70, 201)
x2 = linspace(1, 50, 201)
A1 = SparseUnidimensionalInterpolator(ker, 1, x1, 1:n1)
A2 = SparseUnidimensionalInterpolator(ker, 2, x2, 1:n2)
A = A1*A2
```
