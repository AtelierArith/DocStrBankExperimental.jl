```
zero_vector(𝔤::LieAlgebra)
zero_vector(𝔤::LieAlgebra, T::Type)
zero_vector!(𝔤::LieAlgebra, X::T)
```

Generate a [`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`) of type `T` in the [`LieAlgebra`](@ref) $𝔤$ of the [`AbstractLieGroup`](@ref) `G`. By default this calls `zero_vector` on the manifold of `G` at the `identity_element(G,T)`

For the allocating variant the type `T` of the zero vector can be specified.
