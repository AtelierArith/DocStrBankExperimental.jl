```
suitablefor(
    elm::Element, 
    matOrElms::Union{Material, AbstractSet{Element}}, 
    det::Detector; 
    maxE::Float64 = 1.0e6, 
    ampl::Float64 = 1.0e-5,
    warnme::Bool = true
)::Vector{Tuple{Vector{CharXRay}, UnitRange{Int64}}}
```

Given a material or collection of `Element` which ROIs for element `elm` is the material a suitable reference on the detector `det`?   This function provides informational, warning and error messages depending upon the suitability of the material. 
