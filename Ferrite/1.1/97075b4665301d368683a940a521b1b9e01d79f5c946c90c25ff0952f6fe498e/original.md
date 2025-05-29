```
renumber!(dh::AbstractDofHandler, order)
renumber!(dh::AbstractDofHandler, ch::ConstraintHandler, order)
```

Renumber the degrees of freedom in the DofHandler and/or ConstraintHandler according to the ordering `order`.

`order` can be given by one of the following options:

  * A permutation vector `perm::AbstractVector{Int}` such that dof `i` is renumbered to `perm[i]`.
  * [`DofOrder.FieldWise()`](@ref) for renumbering dofs field wise.
  * [`DofOrder.ComponentWise()`](@ref) for renumbering dofs component wise.
  * `DofOrder.Ext{T}` for "external" renumber permutations, see documentation for `DofOrder.Ext` for details.

!!! warning
    The dof numbering in the DofHandler and ConstraintHandler *must always be consistent*. It is therefore necessary to either renumber *before* creating the ConstraintHandler in the first place, or to renumber the DofHandler and the ConstraintHandler *together*.

