```
dscale(dInfo::Dinfo, columns::Vector{Int})
```

データセットの列をスケーリングして、平均0、標準偏差1にします。

ゼロの標準偏差による除算を避けることで、NaNの生成を防ぎます。
