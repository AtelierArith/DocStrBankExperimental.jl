```
poloidal_cocos(c::COCOS, rho, theta, phi) -> NTuple{3}
```

Returns the right-handed poloidal coordinate according to the provided COCOS.

```
cocos.sigma_rhotp = +1 -> (rho, theta, phi)
cocos.sigma_rhotp = -1 -> (rho, phi, theta)
```
