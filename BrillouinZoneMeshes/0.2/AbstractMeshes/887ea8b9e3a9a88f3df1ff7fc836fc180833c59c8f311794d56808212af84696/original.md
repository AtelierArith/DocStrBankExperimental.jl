```
abstract type AbstractMesh{T,DIM} <: AbstractArray{SVector{T,DIM},DIM}
```

Parent type of all meshes in this package.

The default return value of AbstractMesh should be a SVector{T,DIM},  which is assumed to be the cartesian coordinates of the mesh points,  even if the mesh it self is polar.  Other representations of mesh points such as polar coordinates  and fractional coordinates could be provided via getindex with traits.

# Required Fields:

  * `size`: the size of the mesh as a tuple of integers
