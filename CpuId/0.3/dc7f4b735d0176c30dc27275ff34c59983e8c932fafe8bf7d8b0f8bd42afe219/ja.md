```
cpufeature( feature::Symbol ) ::Bool
cpufeature( feature::CpuFeature ) ::Bool
```

CPUに対して、指定された機能をサポートしているかどうかを照会します。高速チェックのために、`CpuId`でグローバル定数として定義された`CpuFeature`を直接提供してください。同じ名前で得られた明示的に型付けされた`CpuFeature`は、対応するシンボルと同じです。 有効なシンボルは`keys(CpuId.CpuFeatureDescription)`から取得できます。
