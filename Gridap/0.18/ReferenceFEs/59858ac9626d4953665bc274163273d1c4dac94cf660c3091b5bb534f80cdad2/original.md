```
abstract type Polytope{D} <: GridapType
```

Abstract type representing a polytope (i.e., a polyhedron in arbitrary dimensions). `D` is the environment dimension (typically, 0, 1, 2, or 3). This type parameter is needed since there are functions in the `Polytope` interface that return containers with `Point{D}` objects. We adopt the [usual nomenclature](https://en.wikipedia.org/wiki/Polytope) for polytope-related objects. All objects in a polytope (from vertices to the polytope itself) are called *n-faces* or simply *faces*. The notation *n-faces* is used only when it is needed to refer to the object dimension n. Otherwise we simply use *face*. In addition, we say

  * vertex (pl. vertices): for 0-faces
  * edge: for 1-faces
  * facet: for (`D-1`)-faces

The `Polytope` interface is defined by overloading the following functions

  * [`get_faces(p::Polytope)`](@ref)
  * [`get_dimranges(p::Polytope)`](@ref)
  * [`Polytope{N}(p::Polytope,faceid::Integer) where N`](@ref)
  * [`get_vertex_coordinates(p::Polytope)`](@ref)
  * [`(==)(a::Polytope{D},b::Polytope{D}) where D`](@ref)

And optionally these ones:

  * [`get_edge_tangent(p::Polytope)`](@ref)
  * [`get_facet_normal(p::Polytope)`](@ref)
  * [`get_facet_orientations(p::Polytope)`](@ref)
  * [`get_vertex_permutations(p::Polytope)`](@ref)
  * [`is_n_cube(p::Polytope)`](@ref)
  * [`is_simplex(p::Polytope)`](@ref)
  * [`simplexify(p::Polytope)`](@ref)

The interface can be tested with the function

  * [`test_polytope`](@ref)
