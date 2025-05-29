```
is_torsion_unit(x::AbsSimpleNumFieldElem, checkisunit::Bool = false) -> Bool
```

$$
x
$$

がトーションユニットであるかどうか、すなわち、$x^n = 1$となる$n$が存在するかどうかを返します。

`checkisunit`が`true`の場合、まず$x$がその数体の最大順序のユニットであるかどうかがチェックされます。
