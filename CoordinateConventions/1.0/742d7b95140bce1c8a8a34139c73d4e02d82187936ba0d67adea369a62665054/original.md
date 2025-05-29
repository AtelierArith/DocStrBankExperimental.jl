```
cylindrical_cocos(c::COCOS, r, phi, z) -> NTuple{3}
```

Returns the right-handed cylindrical coordinate according to the provided COCOS.

```
cocos.sigma_RpZ = +1 -> (r, phi, z)
cocos.sigma_RpZ = -1 -> (r, z, phi)
```
