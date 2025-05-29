```
poloidal_cocos_indices(c::COCOS) -> NTuple{3}
```

指定された COCOS に対して、rho、theta、および phi 座標のインデックスをそれぞれ返します。

```
cocos.sigma_rhotp = +1 -> (1, 2, 3)
cocos.sigma_rhotp = -1 -> (1, 3, 2)
```
