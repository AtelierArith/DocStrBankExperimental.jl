```
OddEvenAsphericSurface(semidiameter, curvature::T, conic::T, aspherics::Vector{T}; normradius::T=semidiameter)
```

Surface incorporating an aspheric polynomial - radius, conic and aspherics are defined relative to absolute semi-diameter.

`aspherics` should be an array of the both odd and even coefficients of the aspheric polynomial starting with A1
