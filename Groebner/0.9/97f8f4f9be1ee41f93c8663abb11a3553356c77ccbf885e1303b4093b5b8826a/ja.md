```
dimension(polynomials; options...)
```

`polynomials`によって生成されたイデアルの（クルル）次元を計算します。

入力がグレブナー基底でない場合、グレブナー基底を計算します。

## 引数

  * `polynomials`: 多項式の配列。AbstractAlgebra.jl、Nemo.jl、およびDynamicPolynomials.jlの多項式をサポートします。

## 戻り値

  * `dimension`: 整数、次元。

## 例

AbstractAlgebra.jlを使用して:

```@example
using Groebner, Nemo
R, (x, y) = QQ["x", "y"]
dimension([x*y^2 + x, y*x^2 + y])
```

## 注意事項

  * この関数はスレッドセーフです。
  * AbstractAlgebra.jlおよびNemo.jlの場合、この関数は`GF(p)`、`Native.GF(p)`、および`QQ`の多項式に対して最も効率的です。

```
