```
paramgb(polys; options...) -> basis
```

`polys`によって生成されたイデアルのグレブナー基底を計算します。引数`polys`は、有理数の有理関数の体または有限体上の多項式の配列でなければなりません。

アルゴリズムは確率的であり、高い確率で成功します。

## オプション

サポートされているキーワード引数：

  * `ordering`: モノミアルの順序。**Groebner.jl**と同様で、例えば`Lex()`や`DegRevLex()`など。
  * `up_to_degree`: 分子と分母の合計次数が固定の値までのパラメータを計算します。例：`up_to_degree=(2, 2)`。**注意:** `up_to_degree`が指定されている場合、基底の係数はその合計次数が`up_to_degree`以下である場合にのみ正しいことが保証されます。それ以外の場合、基底の係数は`1`に設定されます。
  * `rational_interpolator`: 有理関数補間アルゴリズム。可能なオプションは`:CuytLee`と`:VanDerHoevenLecerf`（デフォルト）です。
  * `estimate_degrees`: `true`の場合、補間を開始する前にパラメータの合計次数を推定します。デフォルトは`true`です。
  * `assess_correctness`: `true`の場合、基底が高い確率で正しいことを確認します。デフォルトは`true`です。**注意**：

## 例

```jldoctest
using Nemo, ParamPunPam

Rparam, (a, b) = polynomial_ring(QQ, ["a", "b"])
R, (x, y, z) = polynomial_ring(fraction_field(Rparam), ["x", "y", "z"])

ParamPunPam.paramgb([a*x^2 + 1, y^2*z + (1//b)*y])
```
