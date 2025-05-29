```
Lex()
Lex(variables)
Lex(variables...)
```

辞書式単項式順序。

私たちは、Martin Kreuzer、Lorenzo Robbianoによる『Computational Commutative Algebra 1』の第1章からの定義を使用します。DOI: https://doi.org/10.1007/978-3-540-70628-1。

*Dura Lex, sed Lex.*

## 例

```@example
using Groebner, AbstractAlgebra
R, (x, y) = QQ["x", "y"];

# x > y の辞書式順序
groebner([x*y + x, x + y^2], ordering=Lex())

# y > x の辞書式順序
groebner([x*y + x, x + y^2], ordering=Lex([y, x]))

# x > y の辞書式順序
# 両方の構文が許可されています -- Lex([...]) と Lex(...)
groebner([x*y + x, x + y^2], ordering=Lex(x, y))
```
