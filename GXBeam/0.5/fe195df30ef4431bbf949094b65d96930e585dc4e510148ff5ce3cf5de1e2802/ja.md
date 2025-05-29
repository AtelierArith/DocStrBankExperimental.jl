```
Material(E1, E2, E3, G12, G13, G23, nu12, nu13, nu23, rho,
    S1t=1.0, S1c=1.0, S2t=1.0, S2c=1.0, S3t=1.0, S3c=1.0, S12=1.0, S13=1.0, S23=1.0)
```

異方性材料特性。軸1は主プライ軸、軸2は横プライ軸、軸3はプライに垂直です。繊維の方向がゼロの場合、軸1はビーム軸に沿っています。

# 引数

  * `Ei::float`: i軸に沿ったヤング率。
  * `Gij::float`: せん断弾性率
  * `nuij::float`: ポアソン比。  $nu_ij E_j = nu_ji E_i$
  * `rho::float`: 密度
  * `Sit::float`: i方向の引張強度
  * `Sic::float`: i方向の圧縮強度
  * `Sij::float`: ij方向の強度
