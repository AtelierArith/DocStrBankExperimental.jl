```
normalform(basis, to_be_reduced; options...)
```

多項式 `to_be_reduced` の正規形をグレブナー基底 `basis` に関して計算します。

## 引数

  * `basis`: 多項式の配列、グレブナー基底。AbstractAlgebra.jl、Nemo.jl、およびDynamicPolynomials.jlの多項式をサポートします。
  * `to_be_reduced`: 単一の多項式または多項式の配列。AbstractAlgebra.jl、Nemo.jl、およびDynamicPolynomials.jlの多項式をサポートします。

## 戻り値

  * `reduced`: 単一の多項式または多項式の配列、正規形です。

## 可能なオプション

  * `check`: `basis` がグレブナー基底を形成するかどうかを確認します。デフォルトは `true` です。
  * `ordering`: モニモアルの順序を指定します。利用可能なモニモアルの順序は次のとおりです：

      * `InputOrdering()` は与えられた `polynomials` から順序を推測します（デフォルト）、
      * `Lex()` は辞書式順序、
      * `DegLex()` は次数辞書式順序、
      * `DegRevLex()` は次数逆辞書式順序、
      * `WeightedOrdering(weights)` は重み付き順序、
      * `ProductOrdering(args...)` はブロック順序、
      * `MatrixOrdering(matrix)` は行列順序です。

    詳細と例については、対応するドキュメントページを参照してください。

## 例

単一の多項式の正規形を求める：

```@example
using Groebner, DynamicPolynomials
@polyvar x y;
normalform([y^2 + x, x^2 + y], x^2 + y^2 + 1)
```

または、2つの多項式を同時に簡約する：

```@example
using Groebner, DynamicPolynomials
@polyvar x y;
normalform([y^2 + x, x^2 + y], [x^2 + y^2 + 1, x^10*y^10])
```

## 注意事項

  * この関数はスレッドセーフです。
  * AbstractAlgebra.jl と Nemo.jl の場合、この関数は `GF(p)`、`Native.GF(p)`、および `QQ` 上の多項式に対して最も効率的です。
  * デフォルトのアルゴリズムは確率的です（`certify=false`）。結果は高い確率で正しいですが、確率の正確な上限は知られていません。
