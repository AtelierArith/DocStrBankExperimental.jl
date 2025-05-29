```
mask = skbr(A; iterations=10)
```

Applies recursive skewness balancing by *Bartels e.a (2006)* [^bartels2006] to `A`. Applies `skb` `iterations` times to the object (non-terrain) mask, as to include more (sloped) terrain.

# Output

  * `mask::BitMatrix` Mask of allowed values

[^bartels2006]: Bartels, M., Hong Wei, and D.C. Mason. 2006. “DTM Generation from LIDAR Data Using Skewness Balancing.” In 18th International Conference on Pattern Recognition (ICPR’06), 1:566–69. https://doi.org/10/cwk4v2.
