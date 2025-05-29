`find`(n, points, printformulaq = false)

与えられた点を使用してn次導関数の公式を計算します。

入力として、`n`と`points`（[`compute`]を参照）には、-2 : 3や[-2, -1, 0, 1, 2, 3]のように両端点を使用する公式が存在しない場合があります。この場合、`find`は範囲を縮小して、最初に-1 : 3、次に-2 : 2、次に-1 : 2、というように、公式が見つかるまで、または全く公式が見つからないまで試みます。

[`compute`]、[`findbackward`]、および[`findforward`]も参照してください。

# 例

```
import FiniteDifferenceFormula as fd
fd.find(2, -10:9)
```
