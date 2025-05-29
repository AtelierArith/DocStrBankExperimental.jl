```
cylindrical_cocos(c::COCOS, r, phi, z) -> NTuple{3}
```

提供されたCOCOSに従って、右手系の円筒座標を返します。

```
cocos.sigma_RpZ = +1 -> (r, phi, z)
cocos.sigma_RpZ = -1 -> (r, z, phi)
```
