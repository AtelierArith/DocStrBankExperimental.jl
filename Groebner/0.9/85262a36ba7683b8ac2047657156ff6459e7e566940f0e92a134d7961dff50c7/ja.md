```
groebner(polynomials; options...)
```

`polynomials`によって生成されたイデアルのグレブナー基底を計算します。

## 引数

  * `polynomials`: 多項式の配列。AbstractAlgebra.jl、Nemo.jl、およびDynamicPolynomials.jlの多項式をサポートします。

## 戻り値

  * `basis`: 多項式の配列、グレブナー基底。

## 可能なオプション

  * `reduced`: ブール値、返される基底が自動的に簡約され、一意である必要があるかどうか。デフォルトは`true`。
  * `ordering`: モノミアルの順序を指定します。利用可能なモノミアル順序は次のとおりです：

      * `InputOrdering()`は、与えられた`polynomials`から順序を推測します（デフォルト）、
      * `Lex(args...)`は、辞書式順序、
      * `DegLex(args...)`は、次数辞書式順序、
      * `DegRevLex(args...)`は、次数逆辞書式順序、
      * `WeightedOrdering(args...)`は、重み付け順序、
      * `ProductOrdering(args...)`は、ブロック順序、
      * `MatrixOrdering(args...)`は、行列順序。

    詳細と例については、対応するドキュメントページを参照してください。
  * `certify`: ブール値、得られた基底を証明するかどうか。このオプションが`false`の場合、アルゴリズムはランダム化され、結果は高い確率で正しいです。このオプションが`true`の場合、理想が同次である場合に結果が正しいことが保証されます。デフォルトは`false`。
  * `linalg`: 線形代数バックエンドのシンボル。利用可能なオプションは次のとおりです：

      * `:auto`は、自動選択（デフォルト）、
      * `:deterministic`は、決定論的スパース線形代数、
      * `:randomized`は、確率的スパース線形代数。
  * `threaded`: マルチスレッドの使用。利用可能なオプションは次のとおりです：

      * `:auto`は、自動選択（デフォルト）、
      * `:no`は、マルチスレッドを決して使用しない、
      * `:yes`は、マルチスレッドの使用を許可する。

    さらに、環境変数`GROEBNER_NO_THREADED`を`1`に設定することで、Groebner.jlでのすべてのマルチスレッドを無効にすることができます。この場合、環境変数が`threaded`オプションよりも優先されます。
  * `monoms`: 計算に使用されるモノミアル表現。利用可能なオプションは次のとおりです：

      * `:auto`は、自動選択（デフォルト）、
      * `:dense`は、古典的な密な指数ベクトル、
      * `:packed`は、パックされた表現。
  * `modular`: モジュラー計算アルゴリズム。有理数上で基底を計算する場合にのみ効果があります。利用可能なオプションは次のとおりです：

      * `:auto`は、自動選択（デフォルト）、
      * `:classic_modular`は、古典的なマルチモジュラーアルゴリズム、
      * `:learn_and_apply`は、学習と適用アルゴリズム。
  * `seed`: ランダム化のためのシード。デフォルトは`42`。
  * `homogenize`: アルゴリズムにおける同次化の使用を制御します。利用可能なオプションは次のとおりです：

      * `:auto`は、自動選択（デフォルト）。
      * `:yes`は、入力理想を常に同次化する、
      * `:no`は、入力理想を決して同次化しない、

## 例

DynamicPolynomials.jlを使用する：

```@example
using Groebner, DynamicPolynomials
@polyvar x y
groebner([x*y^2 + x, y*x^2 + y])
```

AbstractAlgebra.jlを使用する：

```@example
using Groebner, AbstractAlgebra
R, (x, y) = QQ["x", "y"]
groebner([x*y^2 + x, y*x^2 + y])
```

Nemo.jlを使用する：

```@example
using Groebner, Nemo
R, (x, y) = GF(2^30+3)["x", "y"]
groebner([x*y^2 + x, y*x^2 + y])
```

または、別のモノミアル順序で：

```@example
# y > xのlex
groebner([x*y^2 + x, y*x^2 + y], ordering=Lex(y, x))

# 次数逆辞書式
groebner([x*y^2 + x, y*x^2 + y], ordering=DegRevLex())
```

## 注意事項

  * この関数はスレッドセーフです。
  * AbstractAlgebra.jlおよびNemo.jlの場合、この関数は`GF(p)`、`Native.GF(p)`、および`QQ`の多項式に対して最も効率的です。
  * デフォルトのアルゴリズムは確率的です（`certify=false`）。結果は高い確率で正しいですが、確率に関する正確な境界は知られていません。

```
