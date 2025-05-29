Requires `import DataFrame`

```
NeXLMatrixCorrection.zaf(mat::Material, e0::AbstractFloat, toa::AbstractFloat=deg2rad(40.0); 
    mc::Type{<:MatrixCorrection} = XPP, fc::Type{<:FluorescenceCorrection}=ReedFluorescence, coatings::Dict{String,Film}=Dict{String,Film}(), stds::Dict{Element,Material}=Dict{Element,Material}(), minweight=0.01)

NeXLMatrixCorrection.zaf(ir::IterationResult; minweight=0.01)
```
