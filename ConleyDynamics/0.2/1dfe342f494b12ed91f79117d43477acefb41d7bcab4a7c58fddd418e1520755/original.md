```
plot_planar_cubical_morse(cc::LefschetzComplex,
                          fname::String,
                          morsesets::CellSubsets;
                          [hfac::Real=1.2,]
                          [vfac::Real=1.2,]
                          [cubefac::Real=0,]
                          [pdim::Vector{Bool}=[false,true,true],]
                          [pv::Bool=false])
```

Create an image of a planar cubical complex, together with Morse sets, or also selected multivectors.

This is an alternative method which does not require the specification of the vertex coordinates. They will be taken from the cube vertex labels.
