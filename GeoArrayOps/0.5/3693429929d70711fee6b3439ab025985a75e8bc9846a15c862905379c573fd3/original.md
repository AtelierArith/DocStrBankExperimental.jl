```
mask = skb(A; mean=mean(A))
```

Applies skewness balancing by *Bartels e.a (2006)* [^bartels2006] to `A`. Improved the performance by applying a binary search to find the threshold value.

# Output

  * `mask::BitMatrix` Mask of allowed values

[^bartels2006]: Bartels, M., Hong Wei, and D.C. Mason. 2006. “DTM Generation from LIDAR Data Using Skewness Balancing.” In 18th International Conference on Pattern Recognition (ICPR’06), 1:566–69. https://doi.org/10/cwk4v2.
