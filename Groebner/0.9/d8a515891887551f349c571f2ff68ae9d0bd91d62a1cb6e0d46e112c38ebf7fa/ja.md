```
groebner_with_change_matrix(polynomials; options...)
```

`polynomials`によって生成されたイデアルのグレブナー基底を計算し、元の生成子から基底要素へのマップである変更行列を出力します。

## 引数

  * `polynomials`: 多項式の配列。AbstractAlgebra.jl、Nemo.jl、およびDynamicPolynomials.jlの多項式をサポートします。AbstractAlgebra.jlおよびNemo.jlの場合、多項式の係数は`GF(p)`、`Native.GF(p)`、または`QQ`に属する必要があります。

## 戻り値

タプル（`basis`、`matrix`）を返します。

  * `basis`: 多項式の配列、グレブナー基底。
  * `matrix`: 行列で、`matrix * polynomials == basis`が成り立ちます。

## 可能なオプション

`groebner`と同じです。

## 例

AbstractAlgebra.jlを使用して:

```@example
using Groebner, AbstractAlgebra
R, (x, y) = QQ["x", "y"]
f = [x*y^2 + x, y*x^2 + y]

g, m = groebner_with_change_matrix(f, ordering=DegRevLex())

@assert isgroebner(g, ordering=DegRevLex())
@assert m * f == g
```

## 注意事項

  * `DegRevLex`順序のみがサポートされています。
  * この関数はスレッドセーフです。
  * デフォルトのアルゴリズムは確率的です（`certify=false`）。結果は高い確率で正しいですが、確率に関する正確な境界は知られていません。
