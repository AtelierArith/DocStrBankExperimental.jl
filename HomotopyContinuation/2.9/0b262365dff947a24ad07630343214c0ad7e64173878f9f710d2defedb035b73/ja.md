```
geodesic_distance(A::LinearSubspace, B::LinearSubspace)
```

`A`と`B`の間の測地線距離を計算します。ここで、`A`は線形部分空間、`B`は線形部分空間であり、`k = dim(A)`、`n`は周囲の次元です。これは、[^^LKK19]の導出に従います。

[^LKK19]: Lim, Lek-Heng, Ken Sze-Wai Wong, and Ke Ye. "Numerical algorithms on the affine Grassmannian." SIAM Journal on Matrix Analysis and Applications 40.2 (2019): 371-393.
