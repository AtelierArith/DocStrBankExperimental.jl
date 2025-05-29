```
regiongeog(GI)::Tuple
```

投影された `GI` オブジェクトの限界を地理座標に変換した (lon*min, lon*max, lat*min, lat*max) のタプルを返します。`GI` に登録された参照システムがない場合は空のタプルを返します。`GI` は `GMTgrid`、`GMTimage`、またはそれらのタイプのファイル名 (String) のいずれかです。
