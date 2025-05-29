```
abstract type AbstractTensorMap{T<:Number, S<:IndexSpace, N₁, N₂} end
```

Abstract supertype of all tensor maps, i.e. linear maps between tensor products of vector spaces of type `S<:IndexSpace`, with element type `T`. An `AbstractTensorMap` maps from an input space of type `ProductSpace{S, N₂}` to an output space of type `ProductSpace{S, N₁}`.
