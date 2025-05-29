```
HausdorffDistance(dist::SemiMetric)
```

Hausdorff distance is defined as the maximum of the minimum between two clouds of points.

$$
Hausdorff(U, V) = \max{\max_{u \in U} nndist(u, V), \max{v \in V} nndist(v, U) }
$$

where $nndist(u, V)$ computes the distance of $u$ to its nearest neighbor in $V$ using the `dist` metric.
