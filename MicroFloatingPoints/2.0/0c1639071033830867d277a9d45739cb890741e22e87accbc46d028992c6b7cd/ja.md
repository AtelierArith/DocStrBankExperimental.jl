```
fractional_even(x::Floatmu{szE,szf}) where {szE,szf}
```

`x` の小数部分の最右ビットがゼロであれば `true` を返します。

注意: この関数は `x` が NaN または無限大の値であるかどうかをチェックしません。
