```
b = bounds(ncvar::NCDatasets.CFVariable)
```

変数 `ncvar` の `bounds` 属性に対応する CFVariable を返します。`ncvar` の時間単位とカレンダーが使用されますが、データのパッキングを制御する属性 `scale_factor`、`add_offset`、および `_FillValue` は使用されません。
