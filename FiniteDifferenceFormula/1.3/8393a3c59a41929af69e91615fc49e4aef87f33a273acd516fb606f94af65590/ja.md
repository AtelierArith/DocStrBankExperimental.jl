`truncationerror`()

最後に計算された式の切り捨て誤差をビッグオー記法で示します。

# 例

```
import FiniteDifferenceFormula as fd
fd.compute(2,-3:3)
fd.truncationerror()
fd.find(3,[-2, 1, 2, 5, 7, 15])
fd.truncationerror()
```
