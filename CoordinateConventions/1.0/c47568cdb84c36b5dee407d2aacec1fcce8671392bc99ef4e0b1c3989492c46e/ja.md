```
poloidal_cocos(c::COCOS, rho, theta, phi) -> NTuple{3}
```

提供されたCOCOSに従って、右手系のポロイダル座標を返します。

```
cocos.sigma_rhotp = +1 -> (rho, theta, phi)
cocos.sigma_rhotp = -1 -> (rho, phi, theta)
```
