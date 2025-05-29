```
tofloat(intpoint, magnitude, precision)
```

指定されたマグニチュードと精度を使用して、IntPointを浮動小数点値に復元します。 magnitude = ゼロを超える桁数 (90 => 2, 9 => 1, 0.9 => 0, 0.09 => -1) sigdigits = 保存された桁数 (94.3856で4 => 94.39)
