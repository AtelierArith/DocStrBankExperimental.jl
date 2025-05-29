```
T = intensitytype(scan)
```

意図を表すために使用される型を返します（イオンカウント）。

パッケージは、スキャンタイプに対してこれを定義する必要があります。すなわち、

```
MzCore.intensitytype(::Type{SomeScanType{T,...}}) = T
```
