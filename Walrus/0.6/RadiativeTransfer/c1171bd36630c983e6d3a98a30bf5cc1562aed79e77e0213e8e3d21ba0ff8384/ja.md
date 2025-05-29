```
HomogeneousBodyHeating
```

単一バンド光減衰のモデルで、水を次の形で加熱します：

$$
I(x, y, z) = I_0(x, y) * \exp\left(-\alpha z\right),
$$

ここで、$I$は放射強度、$\alpha$は減衰係数です。これは水を次のように加熱します：$\frac{\partial T(x, y, z)}{\partial t} = \frac{I(x, y, z)A}{c^p\rho}$、ここで$A$はセルの面積、$c^p$は比熱容量、$\rho$は水の密度です。
