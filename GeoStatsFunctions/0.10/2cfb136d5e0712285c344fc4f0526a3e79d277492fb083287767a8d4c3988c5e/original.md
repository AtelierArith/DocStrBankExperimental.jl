```
EmpiricalVariogramSurface(data, var₁, var₂=var₁;
                          normal=Vec(0,0,1), nangs=50,
                          ptol=0.5u"m", dtol=0.5u"m",
                          [options])
```

Given a `normal` direction, estimate the (cross-)variogram of variables `var₁` and `var₂` along all directions in the corresponding plane of variation.

Optionally, specify the tolerance `ptol` in length units for the plane partition, the tolerance `dtol` in length units for the direction partition, the number of angles `nangs` in the plane, and forward the `options` to the underlying [`EmpiricalVariogram`](@ref).
