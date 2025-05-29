```
queryDiscRing(resol::Resolution, theta, phi, radius; fact=0)
```

中心が方向 `(theta, phi)` から `radius` よりも近いピクセルのインデックスのリストを返します。3つの角度 `radius`、`theta`、および `phi` はラジアンで表現する必要があります。

`fact` がゼロでない場合、それは正の整数でなければならず、`fact * nside` の解像度で計算を行う必要があります。
