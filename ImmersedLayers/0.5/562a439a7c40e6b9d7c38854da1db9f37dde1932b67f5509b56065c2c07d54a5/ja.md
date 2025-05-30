```julia
struct BasicILMCache{N, SCA<:ImmersedLayers.AbstractScalingType, GCT, ND, BLT<:RigidBodyTools.BodyList, NT<:CartesianGrids.VectorData, DST<:CartesianGrids.ScalarData, REGT<:CartesianGrids.Regularize, RSNT<:CartesianGrids.RegularizationMatrix, ESNT<:CartesianGrids.InterpolationMatrix, RT<:CartesianGrids.RegularizationMatrix, ET<:CartesianGrids.InterpolationMatrix, RCT, ECT, RDT, EDT, LT<:CartesianGrids.Laplacian, GVT, GNT, GDT, SVT, SDT, SST} <: ImmersedLayers.AbstractBasicCache{N, GCT}
```

表面操作に使用する演算子とストレージデータのキャッシュ。[`SurfaceScalarCache`](@ref)または[`SurfaceVectorCache`](@ref)を使用して構築されます。
