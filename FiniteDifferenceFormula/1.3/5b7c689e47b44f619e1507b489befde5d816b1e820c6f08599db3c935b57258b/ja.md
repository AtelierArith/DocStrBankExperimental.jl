`taylorcoefs`(j, n = 10))

f(x[i + j]) = f(x[i] + jh) のテイラー級数の最初の n 項の係数を計算して返します。ここで、h は x の増分です。

# 例

```
import FiniteDifferenceFormula as fd
fd.taylorcoefs(-2)
fd.taylorcoefs(5, 4)
```
