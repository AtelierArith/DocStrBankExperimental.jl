```
is_torsion_unit(x::AbsSimpleNumFieldOrderElem, checkisunit::Bool = false) -> Bool
```

$$
x
$$

がトーションユニットであるかどうか、すなわち、$x^n = 1$となる$n$が存在するかどうかを返します。

`checkisunit`が`true`の場合、最初に$x$が$x$が属する数体の最大順序のユニットであるかどうかがチェックされます。
