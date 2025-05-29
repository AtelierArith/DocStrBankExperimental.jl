```
abstract type ReferenceFE{D} <: GridapType
```

Abstract type representing a Reference finite element. `D` is the underlying coordinate space dimension. We follow the Ciarlet definition. A reference finite element is defined by a polytope (cell topology), a basis of an interpolation space of top of this polytope (denoted here as the prebasis), and a basis of the dual of this space (i.e. the degrees of freedom). From this information one can compute the shape functions (i.e, the canonical basis of w.r.t. the degrees of freedom) with a simple change of basis. In addition, we also encode in this type information about how the interpolation space in a reference finite element is "glued" with neighbors in order to build conforming cell-wise spaces.

The `ReferenceFE` interface is defined by overloading these methods:

  * [`num_dofs(reffe::ReferenceFE)`](@ref)
  * [`get_polytope(reffe::ReferenceFE)`](@ref)
  * [`get_prebasis(reffe::ReferenceFE)`](@ref)
  * [`get_dof_basis(reffe::ReferenceFE)`](@ref)
  * [`Conformity(reffe::ReferenceFE)`](@ref)
  * [`get_face_own_dofs(reffe::ReferenceFE,conf::Conformity)`](@ref)
  * [`get_face_own_dofs_permutations(reffe::ReferenceFE,conf::Conformity)`](@ref)
  * [`get_face_dofs(reffe::ReferenceFE)`](@ref)

The interface is tested with

  * [`test_reference_fe(reffe::ReferenceFE)`](@ref)
