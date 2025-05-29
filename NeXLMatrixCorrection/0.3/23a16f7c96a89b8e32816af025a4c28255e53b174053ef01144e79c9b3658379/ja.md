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

指定された測定のためにKRatioオブジェクトを構築します。:BeamEnergyおよび:TakeOffAngleプロパティは必須です。:Coatingプロパティはオプションです。
