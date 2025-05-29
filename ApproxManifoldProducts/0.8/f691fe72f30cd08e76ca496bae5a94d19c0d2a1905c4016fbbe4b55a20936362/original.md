```julia
getManifoldPartial(M, partial; ...)
getManifoldPartial(M, partial, repr; ...)
getManifoldPartial(M, partial, repr, offset; doError)

```

A so-called full dimension manifold can possibly be reduced to smaller partial manifolds over  some of the dimensions, returning a new programatically generated `<:AbstractManifold`. This funciton can optionally also reduce a point representation for the desired  partial dimensions too.

Example

```julia
using Manifolds
using ApproxManifoldProducts

# a familiar manifold of translation and rotation in 2D
M = SpecialEuclidean(2)


# make a new partial of only the translation components
M_x, _ = getManifoldPartial(M,[1;])
# returns a new TranslationGroup(1) corresponding to just x dimension

# representation is semidirect product of translation and rotation matrix
u0 = ArrayPartition([0.0;0],[1 0; 0 1.0])

# known coordinates are [x,y,θ], eg
#   vee(M,identity_element(M,u0),log(M,identity_element(M,u0),u0))
#   [0;0;0] in this example

# make another new partial of only the rotation component
M_rot, u_rot = getManifoldPartial(M,[3],u0)
# returns SpecialOrthogonal(2) information

# make another new partial of only  y and θ
M_yθ, u_yθ = getManifoldPartial(M,[2;3],u0)
# returns new manifold information as ProductArray(TranslationGroup(1),SpecialOrthogonal(2))
```

Notes

  * Partial dimensions of interest are defined via a `AbstractVector{Int}` of coordinate dimensions.
  * assumed to follow coordinates as transition step towards more general solution
  * assume ProductManifold is the only way to stitch multiple manifolds together
  * Still experimental.

DevNotes

  * FIXME any semidirect product or action information is lost and naive Product manifold assumptions are currently made.

Related

[`getManifold`](@ref), [`AbstractManifold`], [`ProductManifold`], [`GroupManifold`], [`ArrayPartition`]
