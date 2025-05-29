```
HausdorffDistance(dist::SemiMetric)
```

ハウスドルフ距離は、2つの点の集合の間の最小値の最大値として定義されます。

$$
Hausdorff(U, V) = \max{\max_{u \in U} nndist(u, V), \max{v \in V} nndist(v, U) }
$$

ここで、$nndist(u, V)$は、`dist`メトリックを使用して、$u$から$V$内の最近傍までの距離を計算します。
