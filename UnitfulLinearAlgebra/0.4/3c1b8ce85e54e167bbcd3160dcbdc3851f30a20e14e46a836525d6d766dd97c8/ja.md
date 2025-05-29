```
struct UnitfulDimMatrix

DimensionalData.DimArrayに基づいています。
単位次元（範囲とドメイン）のために`unitdims`を追加します。
幾何学的解釈のためにtrueとなる`exact::Bool`を追加します。
```

struct UnitfulDimMatrix{T,N,UD<:Tuple,D<:Tuple,R<:Tuple,A<:AbstractArray{T,N},Na,Me} <: AbstractUnitfulDimVecOrMat{T,N,UD,D,A}     data::A     unitdims::UD     dims::D     refdims::R     name::Na     metadata::Me     exact::Bool     UnitfulDimMatrix(data,unitdims,dims,refdims,name,metadata,exact) = (eltype(parent(data)) <: Quantity) ? error("units not allowed in UnitfulDimMatrix data field") : new{eltype(data),ndims(data),typeof(unitdims),typeof(dims),typeof(refdims),typeof(data)}(data,unitdims,dims,refdims,name,metadata,exact)
