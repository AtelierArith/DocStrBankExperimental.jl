```
RodObstacle(p1, p2, radius; inverted = false) <: AbstractObstacle
```

点 `p1` と `p2` の間に厚さ `2*radius` の球円柱状の棒を構築します。`inverted = true` の場合、障害物は球円柱を*除く*全ての空間です。
