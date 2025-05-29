```
PeriodicDirichlet(u::Symbol, facet_mapping, components=nothing)
PeriodicDirichlet(u::Symbol, facet_mapping, R::AbstractMatrix, components=nothing)
PeriodicDirichlet(u::Symbol, facet_mapping, f::Function, components=nothing)
```

Create a periodic Dirichlet boundary condition for the field `u` on the facet-pairs given in `facet_mapping`. The mapping can be computed with [`collect_periodic_facets`](@ref). The constraint ensures that degrees-of-freedom on the mirror facet are constrained to the corresponding degrees-of-freedom on the image facet. `components` specify the components of `u` that are prescribed by this condition. By default all components of `u` are prescribed.

If the mapping is not aligned with the coordinate axis (e.g. rotated) a rotation matrix `R` should be passed to the constructor. This matrix rotates dofs on the mirror facet to the image facet. Note that this is only applicable for vector-valued problems.

To construct an inhomogeneous periodic constraint it is possible to pass a function `f`. Note that this is currently only supported when the periodicity is aligned with the coordinate axes.

See the manual section on [Periodic boundary conditions](@ref) for more information.
