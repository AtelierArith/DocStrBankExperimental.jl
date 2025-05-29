```julia
struct BasicILMCache{N, SCA<:ImmersedLayers.AbstractScalingType, GCT, ND, BLT<:RigidBodyTools.BodyList, NT<:CartesianGrids.VectorData, DST<:CartesianGrids.ScalarData, REGT<:CartesianGrids.Regularize, RSNT<:CartesianGrids.RegularizationMatrix, ESNT<:CartesianGrids.InterpolationMatrix, RT<:CartesianGrids.RegularizationMatrix, ET<:CartesianGrids.InterpolationMatrix, RCT, ECT, RDT, EDT, LT<:CartesianGrids.Laplacian, GVT, GNT, GDT, SVT, SDT, SST} <: ImmersedLayers.AbstractBasicCache{N, GCT}
```

A cache of operators and storage data for use in surface operations. Constructed with [`SurfaceScalarCache`](@ref) or [`SurfaceVectorCache`](@ref).
