```
catmullrom_by_arclength( points )    
catmullrom_by_arclength( points, (min_between_points, max_between_points))
```

与えられた `points` を通る Catmull-Rom フィットを計算します。このとき、点間のノットの数は、その弧の近似アーク長に反比例して変化します。

`arcpoints_min` と `arcpoints_max` は、2つの点の間の任意の1つの弧を指します。
