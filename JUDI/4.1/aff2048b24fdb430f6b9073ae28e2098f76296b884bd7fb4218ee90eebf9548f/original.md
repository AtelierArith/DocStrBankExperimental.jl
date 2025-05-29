```
Model(n, d, o, m; epsilon=nothing, delta=nothing, theta=nothing,
        phi=nothing, rho=nothing, qp=nothing, vs=nothing, nb=40)
```

The parameters `n`, `d`, `o` and `m` are mandatory, whith `nb` and other physical parameters being optional input arguments.

where

`m`: velocity model in slowness squared (s^2/km^2)

`epsilon`: Epsilon thomsen parameter ( between -1 and 1)

`delta`: Delta thomsen parameter ( between -1 and 1 and delta < epsilon)

`theta`: Anisotopy dip in radian

`phi`: Anisotropy asymuth in radian

`rho`: density (g / m^3)

`qp`: P-wave attenuation for visco-acoustic models

`vs`: S-wave velocity for elastic models.

`nb`: Number of ABC points
