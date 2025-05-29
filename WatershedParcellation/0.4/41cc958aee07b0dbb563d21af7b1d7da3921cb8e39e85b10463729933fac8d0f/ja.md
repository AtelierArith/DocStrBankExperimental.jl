```
merge_small_parcels!(px, metric; threshold)
```

`px::Parcellation`内の`minsize`頂点より小さい各`Parcel`について、その隣接するパーセル（もしあれば）を見つけ、エッジが最も弱いもの、すなわち、間隙領域における`metric`（エッジマップなど）の中央値が半径`radius`の近傍の値に対して最も低い値を持つものとマージします。

発生したマージ操作の数を返します。
