```
stereo
```

Stereographic projection between the complex plane and a three-dimensional unit sphere  centered at `[0,0,0]`. The north pole, `[0,0,1]`, corresponds to complex infinity and the  south pole, `[0,0,-1]`, corresponds to `0+0im`.

For a complex number `z`, `stereo(z)` maps `z` to the sphere. This may also be invoked as  `stereo(x,y)`.

For a (unit) three-dimensional vector `v`, `stereo(v)` returns the complex number by projecting  `v` to the complex plane. This may also be invoked as `stereo(x,y,z)`.
