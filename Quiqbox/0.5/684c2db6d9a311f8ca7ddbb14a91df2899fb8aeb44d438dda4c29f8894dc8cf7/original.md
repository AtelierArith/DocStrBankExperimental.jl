```
BasisFunc{T, D, 𝑙, GN, PT} <: FloatingGTBasisFuncs{T, D, 𝑙, GN, PT, 1}
```

A (floating) Gaussian-type basis function with its center assigned to a defined coordinate.

≡≡≡ Field(s) ≡≡≡

`center::SpatialPoint{T, D, PT}`: The `D`-dimensional center.

`gauss::NTuple{GN, GaussFunc{T, <:Any}}`: Gaussian functions within the basis function.

`l::Tuple{LTuple{D, 𝑙}}`: Cartesian representation of the angular momentum. E.g.,  `Quiqbox.LTuple{3, 1}((1, 0, 0))` (X¹Y⁰Z⁰) would correspond to an specific angular momentum  configuration where the sum of all the components is `𝑙=1`.

`normalizeGTO::Bool`: Whether each `GaussFunc` inside will be normalized in calculations.

`param::NTuple{D+GN*2, ParamBox}`： All the tunable parameters stored in the basis function.

≡≡≡ Initialization Method(s) ≡≡≡

```
BasisFunc(cen::SpatialPoint{T, D, PT}, 
          gs::Tuple{AbstractGaussFunc{T}, Vararg{AbstractGaussFunc{T}, GN-1}}, 
          l::Union{Tuple{LTuple{D, 𝑙}}, LTuple{D, 𝑙}}, normalizeGTO::Bool) where 
         {T, D, PT, 𝑙, GN} -> 
BasisFunc{T, D, 𝑙, GN, PT}

BasisFunc(cen::SpatialPoint{T, D, PT}, gs::AbstractGaussFunc{T}, 
          l::Union{Tuple{LTuple{D, 𝑙}}, LTuple{D, 𝑙}}, normalizeGTO::Bool) where 
         {T, D, PT, 𝑙, GN} -> 
BasisFunc{T, D, 𝑙, 1, PT}
```
