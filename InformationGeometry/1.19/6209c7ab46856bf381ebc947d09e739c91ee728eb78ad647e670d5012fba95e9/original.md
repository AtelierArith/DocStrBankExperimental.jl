```
IntersectCube(DM::AbstractDataModel,Cube::HyperCube,Confnum::Real=1.; Dirs::Tuple{Int,Int,Int}=(1,2,3), N::Int=31) -> Vector{Plane}
```

Returns a set of parallel 2D planes which intersect `Cube`. The planes span the directions corresponding to the basis vectors corresponding to the first two components of `Dirs`. They are separated in the direction of the basis vector associated with the third component of `Dirs`. The keyword `N` can be used to approximately control the number of planes which are returned. This depends on whether more (or fewer) planes than `N` are necessary to cover the whole confidence region of level `Confnum`.
