`findbackward`(n, points, printformulaq = false)

与えられた点を使用して、n次導関数の公式を計算します。

入力として、`n`と`points`（[`compute`]を参照）には、-2 : 3や[-2, -1, 0, 1, 2, 3]のように両端点を使用する公式が存在しない場合があります。この場合、`findbackward`は、最初に-2 : 2、次に-2 : 1、次に-2 : 0と、右端点から範囲を縮小することによって公式を見つけようとします。公式が見つかるか、全く見つからないまで続けます。

[`compute`]、[`find`]、および[`findforward`]も参照してください。

# 例

```
import FiniteDifferenceFormula as fd
fd.compute(3,-100:50)
# 出力: ***** 警告: 3, -100:22は公式が見つかるかもしれない入力です。
fd.findbackward(3,-99:50)
# 出力: (3, -99:23, ...)
```
