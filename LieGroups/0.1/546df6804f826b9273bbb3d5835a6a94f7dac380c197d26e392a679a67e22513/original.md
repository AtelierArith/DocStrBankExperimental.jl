```
LieGroup{𝔽, O<:AbstractGroupOperation, M<:AbstractManifold{𝔽}} <:  AbstractLieGroup{𝔽, O, M}
```

Represent a Lie Group $\mathcal G$.

A *Lie Group* $\mathcal G$ is a group endowed with the structure of a manifold such that the group operations $∘: \mathcal G×\mathcal G → \mathcal G$, see [`compose`](@ref) and the inverse operation $⋅^{-1}: \mathcal G → \mathcal G$, see [`inv`](@ref) are smooth, see for example [HilgertNeeb:2012; Definition 9.1.1](@cite).

Lie groups are named after the Norwegian mathematician [Marius Sophus Lie](https://en.wikipedia.org/wiki/Sophus_Lie) (1842–1899).

# Fields

  * `manifold`: an [`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`) $\mathcal M$
  * `op`: an [`AbstractGroupOperation`](@ref) $∘$ on that manifold

# Constructor

```
LieGroup(M::AbstractManifold, op::AbstractGroupOperation)
```

Generate a Lie group based on a manifold `M` and a group operation `op`, where vectors by default are stored in the Lie Algebra.
