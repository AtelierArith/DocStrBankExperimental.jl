```
is_sublattice_with_relations(M::ZZLat, N::ZZLat) -> Bool, QQMatrix
```

$$
N
$$

が$M$の部分格子であるかどうかを返します。この場合、2番目の返り値は行列$B$であり、$B B_M = B_N$が成り立ちます。ここで、$B_M$と$B_N$はそれぞれ$M$と$N$の基底行列です。
