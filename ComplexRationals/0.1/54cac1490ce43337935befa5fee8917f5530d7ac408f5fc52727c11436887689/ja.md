```
is_negative(x::ComplexRational) -> Bool
```

`x`が(c + i·b)/cの形で与えられ、c > 0（そのコンストラクタによって強制される）と仮定すると、この関数はその数が負の符号で表示されるべき場合にtrueを返します。ここでの規則は次の通りです：

  * 実部(a)が非ゼロの場合、a < 0ならtrueを返します。
  * それ以外の場合（aがゼロの場合）、虚部(b)が負であればtrueを返します。

両方がゼロの場合はfalseを返します。
