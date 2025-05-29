```
T = mztype(scan)
```

`m/z` 値を表すために使用される型を返します。

パッケージはスキャンタイプのためにこれを定義する必要があります。すなわち、

```
MzCore.mztype(::Type{SomeScanType{T,...}}) = T
```
