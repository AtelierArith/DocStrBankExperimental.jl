```
cutting(self::RheoTimeData, time_on::Real, time_off::Real)
```

指定された時間間隔の外にあるデータを削除します。

時間間隔（`time_on`、`time_off`）を指定することにより、時間間隔の外にあるデータがない新しい`RheoTimeData`が返されます。
