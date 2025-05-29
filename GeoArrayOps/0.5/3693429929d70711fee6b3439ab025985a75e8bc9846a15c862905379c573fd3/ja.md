```
mask = skb(A; mean=mean(A))
```

*Bartels e.a (2006)* [^bartels2006] によって `A` にスキュー平衡を適用します。閾値を見つけるために二分探索を適用することで性能が向上しました。

# 出力

  * `mask::BitMatrix` 許可された値のマスク

[^bartels2006]: Bartels, M., Hong Wei, and D.C. Mason. 2006. “DTM Generation from LIDAR Data Using Skewness Balancing.” In 18th International Conference on Pattern Recognition (ICPR’06), 1:566–69. https://doi.org/10/cwk4v2.
