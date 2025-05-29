`findforward`(n, points, printformulaq = false)

与えられた点を使用して、n次導関数の公式を計算します。

入力の `n` と `points`（[`compute`]を参照）に対して、-2 : 3や[-2, -1, 0, 1, 2, 3]のように両端点を使用する公式が存在しない場合があります。この場合、`findforward`は、最初に-1 : 3、次に0 : 3、次に1 : 3と、左端点から範囲を縮小して公式を見つけようとします。公式が見つかるか、全く見つからないまで続けます。

[`compute`]、[`find`]、および[`findbackward`]も参照してください。

# 例

```
import FiniteDifferenceFormula as fd
fd.findforward(2, -10:9)
```
