```
distance(t1::Tree, t2::Tree; type = :RF, normalize = false)
```

2つの木の間の距離を計算します。許可されているタイプについては `TreeTools.tree_distance_types` を参照してください。`normalize` が真の場合、距離は `[0,1]` に正規化されます。
