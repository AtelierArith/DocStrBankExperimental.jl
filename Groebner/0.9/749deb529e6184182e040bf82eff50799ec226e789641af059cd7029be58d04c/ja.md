```
isgroebner(polynomials; options...)
```

`polynomials`がグレブナー基底を形成するかどうかをチェックします。

## 引数

  * `polynomials`: 多項式の配列。AbstractAlgebra.jl、Nemo.jl、およびDynamicPolynomials.jlの多項式をサポートしています。

## 戻り値

  * `flag`: `polynomials`が`polynomials`によって生成されたイデアルのグレブナー基底であるかどうかを示すbool値。

## 可能なオプション

  * `ordering`: モノミアルの順序を指定します。利用可能なモノミアル順序は次のとおりです：

      * `InputOrdering()`は与えられた`polynomials`から順序を推測します（デフォルト）、
      * `Lex()`は辞書式順序、
      * `DegLex()`は次数辞書式順序、
      * `DegRevLex()`は次数逆辞書式順序、
      * `WeightedOrdering(weights)`は重み付き順序、
      * `ProductOrdering(args...)`はブロック順序、
      * `MatrixOrdering(matrix)`は行列順序。

    詳細と例については、対応するドキュメントページを参照してください。
  * `certify`: 決定論的アルゴリズムを使用するかどうかを示すbool値。デフォルトは`false`です。
  * `seed`: ランダム化のためのシード。デフォルト値は`42`です。

## 例

`DynamicPolynomials`を使用する：

```@example
using Groebner, DynamicPolynomials
@polyvar x y;
isgroebner([x*y^2 + x, y*x^2 + y])
```

`AbstractAlgebra`を使用する：

```@example
using Groebner, AbstractAlgebra
R, (x, y) = QQ["x", "y"]
isgroebner([x*y^2 + x, y*x^2 + y])
```

## 注意事項

  * この関数はスレッドセーフです。
  * AbstractAlgebra.jlおよびNemo.jlの場合、この関数は`GF(p)`、`Native.GF(p)`、および`QQ`上の多項式に対して最も効率的です。
  * デフォルトのアルゴリズムは確率的です（`certify=false`）。結果は高い確率で正しいですが、確率に関する正確な境界は知られていません。
