`taylor`()

  * 新しく計算された式のテイラー級数の最初のいくつかの非ゼロ項を印刷します（失敗しても）。

`taylor`(j, n = 10)

  * f(x[i+j]) のテイラー級数の最初の n 項を x[i] の周りで印刷します。

`taylor`(coefs, n = 10), または

  * 'coefs' にある係数を持つテイラー級数の最初の n 項を印刷します。

`taylor`(points, k, n::Int = 10)

  * 線形結合のテイラー級数の最初の n の非ゼロ項を印刷します:  k[0]f(x[i+points[0]]) + k[1]f(x[i+points[1]]) + ...

最後の2つは、式が数学的に有効かどうかを確認する別の方法も提供します。

[`verifyformula`], [`activatejuliafunction`], および [`taylorcoefs`] も参照してください。

# 例

```
import FiniteDifferenceFormula as fd
fd.compute(1, [0, 1, 5, 8])
fd.taylor()

fd.taylor(2)

n = 50
coefs = 2*fd.tcoefs(0, n) - 6*fd.tcoefs(1, n) + 4*fd.tcoefs(2, n)
fd.taylor(coefs, n) # この n は任意の正の整数にすることができます

fd.taylor(-fd.tcoefs(0) + 3*fd.tcoefs(1) - 3*fd.tcoefs(2) + fd.tcoefs(3))
fd.taylor(0:3, [-1, 3, -3, 1], 6)
```
