```
DegRevLex()
DegRevLex(variables)
DegRevLex(variables...)
```

次数逆辞書順の単項式順序。

私たちは、Martin Kreuzer、Lorenzo Robbianoによる『Computational Commutative Algebra 1』の第1章からの定義を使用します。DOI: https://doi.org/10.1007/978-3-540-70628-1。

## 例

```@example
using Groebner, AbstractAlgebra
R, (x, y) = QQ["x", "y"];

# x > y の場合の次数逆辞書順
groebner([x*y + x, x + y^2], ordering=DegRevLex())

# y > x の場合の次数逆辞書順
groebner([x*y + x, x + y^2], ordering=DegRevLex(y, x))
```
