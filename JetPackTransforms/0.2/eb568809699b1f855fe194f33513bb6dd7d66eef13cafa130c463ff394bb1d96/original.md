```
A = JopSlantStack(dom[; dz=10.0, dh=10.0, h0=-1000.0, ...])
```

where `A` is the 2D slant-stack operator mapping for `z-h` to `tau-p`.  The domain of the operator is `nz` x `nh` with precision T, `dz` is the depth spacing, `dh` is the half-offset spacing, and `h0` is the origin of the half-offset axis.  The additional named optional arguments along with their default values are,

  * `theta=-60:1.0:60` - range of opening angles.  The ray parameter is: p=sin(theta/2)/c
  * `padz=0.0,padh=0.0` - fractional padding in depth and offset to apply before applying the Fourier transfrom
  * `taperz=(0,0)` - beginning and end taper in the z-direction before transforming from `z-h` to `kz-kh`
  * `taperh=(0,0)` - beginning and end taper in the h-direction before transforming from `z-h` to `kz-kh`
  * `taperkz=(0,0)` - beginning and end taper in the kz-direction before transforming from `kz-kh` to `z-h`
  * `taperkh=(0,0)` - beginning and end taper in the kh-direction before transforming from `kz-kh` to `z-h`

# Notes

  * It should be possible to extend this operator to 3D
  * If your domain is t-h rather than z-h, you can still use this operator
