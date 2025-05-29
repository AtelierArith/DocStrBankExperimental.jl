```
plot_planar_cubical(cc::LefschetzComplex,
                    fname::String;
                    [hfac::Real=1.2,]
                    [vfac::Real=1.2,]
                    [cubefac::Real=0,]
                    [pdim::Vector{Bool}=[true,true,true],]
                    [pv::Bool=false])
```

Create an image of a planar cubical complex.

This is an alternative method which does not require the specification of the vertex coordinates. They will be taken from the cube vertex labels.
