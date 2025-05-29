```
mask = skbr(A; iterations=10)
```

*Bartels e.a (2006)* [^bartels2006] による再帰的な歪みバランスを `A` に適用します。オブジェクト（非地形）マスクに `skb` を `iterations` 回適用し、より多くの（傾斜のある）地形を含めます。

# 出力

  * `mask::BitMatrix` 許可された値のマスク

[^bartels2006]: Bartels, M., Hong Wei, and D.C. Mason. 2006. “DTM Generation from LIDAR Data Using Skewness Balancing.” In 18th International Conference on Pattern Recognition (ICPR’06), 1:566–69. https://doi.org/10/cwk4v2.
