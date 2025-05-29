```
inbox(box::AbstractVector, x::AbstractVector)
```

与えられた位置はボックスの内部ですか？

  * `box` = [minx,maxx,miny,maxy,minz,maxz]として配置されたベクトルエントリ（または低次元空間に合わせて調整されたもの）。

注：ボックスの境界上の点は内部と見なされます。
