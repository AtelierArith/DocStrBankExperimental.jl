```
quotient_basis(polynomials; options...)
```

ゼロ次元イデアルの商代数のモニモニアル基底を返します。

入力がグレブナー基底でない場合、グレブナー基底を計算します。入力がゼロ次元イデアルでない場合、エラーが発生します。

## 引数

  * `polynomials`: 多項式の配列。AbstractAlgebra.jl、Nemo.jl、およびDynamicPolynomials.jlからの多項式をサポートします。

## 戻り値

  * `basis`: モニモニアルの配列、商基底。

## 可能なオプション

  * `ordering`: モニモニアルの順序を指定します。利用可能なモニモニアル順序は次のとおりです：

      * `InputOrdering()` は与えられた `polynomials` から順序を推測します（デフォルト）、
      * `Lex()` は辞書式順序、
      * `DegLex()` は次数辞書式順序、
      * `DegRevLex()` は次数逆辞書式順序、
      * `WeightedOrdering(weights)` は重み付き順序、
      * `ProductOrdering(args...)` はブロック順序、
      * `MatrixOrdering(matrix)` は行列順序。

    詳細と例については、対応するドキュメントページを参照してください。

## 例

AbstractAlgebra.jlを使用：

```@example
using Groebner, Nemo
R, (x, y) = QQ["x", "y"]
quotient_basis([x*y^2 + x, y*x^2 + y])
```

## 注意事項

  * この関数はスレッドセーフです。
  * AbstractAlgebra.jlおよびNemo.jlの場合、この関数は `GF(p)`、`Native.GF(p)`、および `QQ` 上の多項式に対して最も効率的です。
