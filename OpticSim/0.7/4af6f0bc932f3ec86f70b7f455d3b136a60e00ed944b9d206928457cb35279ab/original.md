```
CircularAperture(radius::T, outerhalfsizeu::T, outerhalfsizev::T, surfacenormal::SVector{3,T}, centrepoint::SVector{3,T}; rotationvec::SVector{3,T} = [0.0, 1.0, 0.0])
```

Creates a circular aperture in a rectangle i.e. `FiniteStop{T,CircularStopShape,RectangularStopShape}`. The rotation of the rectangle around its normal is defined by `rotationvec`. `rotationvec×surfacenormal` is taken as the vector along the u axis.
