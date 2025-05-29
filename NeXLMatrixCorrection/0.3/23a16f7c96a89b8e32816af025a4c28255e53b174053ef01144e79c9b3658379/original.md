```
NeXLCore.KRatio(
    cxrs::Vector{CharXRay}, 
    unk_mat::Material, 
    unk_props::Dict{Symbol,Any}, 
    std_mat::Material, 
    std_props::Dict{Symbol,Any};
    mc = XPP,
    fc = ReedFluorescence,
    cc = Coating
)
```

Construct a KRatio object for the specified measurement. The :BeamEnergy and :TakeOffAngle properties are required. The :Coating property is optional.
