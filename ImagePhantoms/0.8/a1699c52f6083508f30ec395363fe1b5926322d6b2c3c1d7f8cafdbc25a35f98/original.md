```
gauss3(cx, cy, cz, wx, wy, wz, Φ=0, Θ=0, value::Number = 1)
gauss3(center::NTuple{3,RealU}, radii::NTuple{3,RealU}=(1,1,1), angle::NTuple{2,RealU}=(0,0), v=1)
gauss3(r, v=1) (isotropic of width `w`)
```

Construct `Object{Gauss3}` from parameters; here `width` = FWHM (full-width at half-maximum).
