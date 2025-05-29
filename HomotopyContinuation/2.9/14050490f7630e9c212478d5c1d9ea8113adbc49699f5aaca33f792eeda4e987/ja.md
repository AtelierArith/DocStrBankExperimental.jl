```
geodesic(A::LinearSubspace, B::LinearSubspace)
```

`A`と`B`を接続する測地線$γ(t)$を返します。これはGrassmanian $Gr(k+1,n+1)$において、$k$は$A$の次元、$n$は周囲の次元です。詳細は[4.3の補題](^LKK19)も参照してください。

[^LKK19]: Lim, Lek-Heng, Ken Sze-Wai Wong, and Ke Ye. "Numerical algorithms on the affine Grassmannian." SIAM Journal on Matrix Analysis and Applications 40.2 (2019): 371-393
