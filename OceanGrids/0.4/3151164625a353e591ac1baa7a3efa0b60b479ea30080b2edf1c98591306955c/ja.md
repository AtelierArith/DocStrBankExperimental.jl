```
vectorize(x3D, grd)
```

`grd`の湿ったボックスにおける`x3D`の3Dフィールドに対応する1Dベクトルを返します。

この関数は本質的に`x3D[iswet(grd)]`を返しますが、いくつかの追加チェックがあります。
